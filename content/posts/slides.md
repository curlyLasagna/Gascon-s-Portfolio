+++
title = 'Slides'
date = 2024-11-03T21:20:31-05:00
+++

I've hosted workshops for the software engineering club at my university using org mode with RevealJs.
## Workshops
- [Markup](https://github.com/curlyLasagna/Markup-Workshop)
- [Terminal](https://github.com/curlyLasagna/Terminal_Workshop)
- [Static Sites](https://github.com/curlyLasagna/Static-Site-Workshop)

Creating a power point presentation felt boring and generic. I wanted to be extra.

I really wanted the following features:
- Code blocks
- Math typesetting

Beamer is a possibility but I'd rather org than $\LaTeX$

Since the end product is a static site, I can host it with GitHub pages so the audience can go through the slides at their own pace.

But I have to be honest, this process takes up more time than using PowerPoint but I need an excuse to visit my good old friend Emacs. 

While I was configuring my Doom Emacs configuration, I ran into the `+present` flag for `org` with the following statement

> A configuration for using org-mode for slide-show presentations or exporting org files to reveal.js slideshows

I was already aware of the power of Emacs, but I was intrigued as to how it's able to create a presentation

```elisp
(org +present)
```

It's described as so: 
>Enable integration with reveal.js, beamer and org-tree-slide, so Emacs can be
 used for presentations. It automatically downloads [reveal.js](https://github.com/hakimel/reveal.js). 

As someone who's constantly trying to justify the use of Emacs, this was the perfect opportunity.

## The process
> I'm going to assume you know how to push to a git repo and set remotes
- I create a directory for the presentation and initialize a git repo
- Create an org file named `index.org`
### Headers
```org
:REVEAL_PROPERTIES:
#+REVEAL_ROOT: https://cdn.jsdelivr.net/npm/reveal.js
#+REVEAL_REVEAL_JS_VERSION: 4
#+REVEAL_PLUGINS: (notes highlight zoom)
#+REVEAL_THEME: white
#+REVEAL_TRANS: linear
:END:
#+OPTIONS: toc:nil num:nil timestamp:nil author:nil
#+TITLE: <insert title>
```

### Exporting to HTML
- I invoke `org-export-dispatch` and select the right options
- This generates an HTML file named `index.html`

## Conclusion 
I really like the look of the slides. I don't enjoy the process of coming up with a layout for my slides and this methodology just checks off a lot of boxes for me.

I do respect PowerPoint and Google Slides for their collaborative features. There's no way I would ever recommend creating slides with others using only text.
