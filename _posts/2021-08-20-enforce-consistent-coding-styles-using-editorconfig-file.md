---
layout: post
title:  "Enforce consistent coding styles using EditorConfig"
date:   2021-08-20 23:00:00 +0200
categories: [go, node.js, php]
---

When working on a project as a team of multiple developers, you might run into the problems of different coding styles, complicating changesets. For example, one developer may indent his braces in a while-loop [using the Allman style](https://en.wikipedia.org/wiki/Indentation_style#Allman_style), while another may [adhere to the K&R style](https://en.wikipedia.org/wiki/Indentation_style#K&R_style). To some this may seem trivial, but when changesets start to get big, this can seriously impact the quality of code reviews, since reviewers have to deal with more code. Once there is a change in a file, it is common, that IDEs format the entire file, which might lead to a lot of unintended changes.

There is a simple solution to this problem and it is called [EditorConfig](https://editorconfig.org/). Basically, EditorConfig provides you with the option of creating a file, that lets you define coding styles for your project. This, .editorconfig, file will then be interpreted by your ide of choice, which will then enforce the standard you defined on your code. That the theory.

## Creating the file

To get started you'll need to create a `.editorconfig` file at root of your project. Next, you are free to specify whatever coding standard you wish. Please refer to [the official EditorConfig specification](https://editorconfig-specification.readthedocs.io/) and the [list of all EditorConfig properties](https://github.com/editorconfig/editorconfig/wiki/EditorConfig-Properties). You may also refer to [well-known projects using EditorConfig](https://github.com/editorconfig/editorconfig/wiki/Projects-Using-EditorConfig) for inspiration.

To host an example we will be give you the following `.editorconfig`:
```
```


## Enforcing the styles


