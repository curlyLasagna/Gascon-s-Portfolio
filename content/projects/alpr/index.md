---
title: "Counting open parking spots"
date: 2024-08-11
---

## About
In my Artificial Intelligence course, our final project was to come up with a problem that AI can be used to solve.

I took this as an opportunity to solve a problem that annoys me as a commuter.

The parking garage shared between the science complex and the math/computer science building at my university doesn't have a system to inform students that there are no parking spots left.

There has been times where I've circled the entirety of the parking garage for a long time, only to give up and park at a parking garage further from my classes.

My ideas was to create a REST API that returns the number of spots available in a parking garage.

We achieved this by using the following technologies:
- Flask as our REST API
- Sqlite to store test data
- easyOCR to read the license plate images
- thefuzz to perform fuzzy string comparison
- opencv for computer vision

The document below will dive deep into greater detail

{{< embed-pdf url="./docs/AI_Term_Project.pdf" >}}
