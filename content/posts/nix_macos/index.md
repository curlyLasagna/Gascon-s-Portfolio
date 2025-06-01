+++
title = 'Standalone Home Manager for MacOS experience'
date = 2025-05-26T21:49:54-04:00
+++

Visit my [dots repo](https://github.com/curlyLasagna/home-managed-dots)

I'm not going to write about how to setup home-manager or nix. There are plenty of resources for that. I'm only sharing my experience.

I might use [nix-darwin](https://github.com/nix-darwin/nix-darwin) in the future. Looks cool.

> [mynixos](https://mynixos.com/home-manager/options) is a really handy reference

## Brew will stay (for now)

Nothing against brew. I just prefer to have a single package manager on my system. It was fun seeing my `brew list` output getting smaller and smaller.

Notable packages that I still depend brew on:

- [Emacs-plus](https://github.com/d12frosted/homebrew-emacs-plus)
  - `brew services` is very convenient in allowing me to run emacs as a daemon
- [ghostty](https://ghostty.org/)
  - nixpkgs' ghostty is currently marked as broken

## GUI apps

I was pleasantly surprised that I was able to run GUI apps installed through nix and the ability to invoke those apps through spotlight. Good stuff!

### nix run
`nix run nixpkgs#...` is also really neat. If you're trying to run an unfree app, you'll have to prepend `NIXPKGS_ALLOW_UNFREE=1` to the `nix run` command and append `--impure`  e.g.

```nix
NIXPKGS_ALLOW_UNFREE=1 nix run nixpkgs#mongodb-compass --impure
```

> If I have a college course that requires me to use a GUI application that I'll never see myself using, I'll use nix run.

### Configuration issue

I converted my json [zed-editor](https://zed.dev/) config to accomodate for home-manager (thanks LLMs). The immutable nature of declaring it in home-manager was limiting zed's features. I couldn't switch the LLM models nor could I set what I want the models to do (ask or write).

I'll just have to put more thought into what applications I should set its configuration as immutable.

## dotfile management

For the example below, `mkOutOfStoreSymlink` to `~/.config/nvim`, which allows me to have mutable neovim config.

Also simplifies the management of dotfiles since the `dots` is within the same repo as my home-manager config

> The problem I have with this setup is that I have to manually go to the config file within the `dots` directory, instead of the usual `cmd + ,` hotkey

```nix
xdg = {
    enable = true;
    configFile = {
      "nvim" = {
        source = config.lib.file.mkOutOfStoreSymlink ./dots/nvim;
      };
      ...
    }
      ...
  }
```
```bash
.
├── dots
│   └── nvim
│       ├── init.lua
│       ├── lazy-lock.json
│       ├── lazyvim.json
│       ├── LICENSE
│       ├── lua
│       │   ├── config
│       │   │   ├── autocmds.lua
│       │   │   ├── keymaps.lua
│       │   │   ├── lazy.lua
│       │   │   └── options.lua
│       │   └── plugins
│       │       └── example.lua
│       ├── README.md
│       └── stylua.toml
├── flake.lock
├── flake.nix
├── home.nix
└── README.md
```

### .text

I personally prefer working with a single file, instead of breaking stuff up to multiple files (if it doesn't hurt). I'd rather search using my text editor than ripgreping and opening up another buffer.

Example of my ghostty config (within `xdg.configFile`):

```
"ghostty/config".text = ''
        command = ${pkgs.fish}/bin/fish --login --interactive
        # Aesthetics
        font-family = ZedMono Nerd Font
        font-size = 13
        window-theme = auto
        ...
      '';
```

Above creates a symlink to where ghostty expects a config file, at `~/.config/ghostty/config`

## Conclusion

nix is tight but it does use a whole lot more storage than brew does but having a declarative config on a repo I could just pull from eases my anxiety in the event that my Macbook stops working.

```bash
🐟 ❯ du -sh /nix/store/
38G     /nix/store/
```
