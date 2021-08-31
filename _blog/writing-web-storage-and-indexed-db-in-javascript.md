---
layout: post
title:  "Writing WebStorage and IndexedDB in JavaScript"
date:   2021-08-31 19:00:00 +0200
tags: ["javascript"]
---

## Comparing WebStorage & IndexedDB

Using the WebStorage API you can write key/value pairs in a handy way to browsers. IndexedDB on the other hand is better used for more structured data and generally if you need a little more than key/value.

## Key/Value using WebStorage

First of all there are two different types of WebStorage:
- Local storage
Data will be stored indefinitely, as long as you don't delete it with JavaScript or you clear the browser cache. 

- Session storage
Stores data only for one session - data will persist until the tab is closed.

