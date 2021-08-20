---
layout: post
title:  "Enforce consistent coding styles using EditorConfig"
date:   2021-08-20 23:00:00 +0200
categories: [go, node.js, php]
---

When working on a project as a team of multiple developers, you might run into the problems of different coding styles, complicating changesets. For example, one developer may indent his braces in a while-loop [using the Allman style](https://en.wikipedia.org/wiki/Indentation_style#Allman_style), while another may [adhere to the K&R style](https://en.wikipedia.org/wiki/Indentation_style#K&R_style). To some this may seem trivial, but when changesets start to get big, this can seriously impact the quality of code reviews, since reviewers have to deal with more code. Once there is a change in a file, it is common, that IDEs format the entire file, which might lead to a lot of unintended changes.

