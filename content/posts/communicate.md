---
title: "Communicate with your team"
description: "Communicate with your team"
type: post
date: 2024-07-31
# weight: 25
# showTableOfContents: true
---

## Context

A co-worker asked for my help with a bug story that she just picked up. I replicated the bug and found out that the client is returning data that the backend doesn't know what to do with. So we have 2 approaches to solving this problem:

1. Change what the client returns to the backend (easier)
2. Change how the backend interacts with the data from the client (harder)

Unfortunately, I decided to go with the harder route because I don't enjoy working with the client's codebase and at that time, I thought that the easier option was the harder option.

## Working towards a crappy solution

I led her down a rabbit hole of modifying the backend, and she even posted a PR where some people agreed with my logic but they didn't have the whole picture, so I can't blame them for that.

Upon testing the functionality, it initially worked, until it ran into different cases and the whole thing fell apart. I expected the tests to fail but modifying the tests to conform to my suggested changes became a bigger struggle.

The lesson of the story: don't be afraid to consult with people in your team. Especially the people who have worked with the system for years. Although I've always nodded in agreement when I hear the tip "ask questions", it seems that I don't practice that skill enough or I need to improve my question-asking ability.
