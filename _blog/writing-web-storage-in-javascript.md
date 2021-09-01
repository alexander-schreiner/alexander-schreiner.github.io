---
layout: post
title:  "Writing WebStorage in JavaScript"
date:   2021-08-31 19:00:00 +0200
tags: ["javascript"]
---

## Comparing WebStorage

Using the WebStorage API, you can write key/value pairs in a handy way to browsers. This technique may be used, depending on the use-case, instead of cookies. You will find WebStorage to be very easy to deal with.

## Key/Value using WebStorage

First of all there are two different types of WebStorage:
- Local storage: Data will be stored indefinitely, as long as you don't delete it with JavaScript or you clear the browser cache. 

- Session storage: Stores data only for one session - data will persist until the tab is closed.

Let's dive into an example using local storage:
```javascript
localStorage.getItem("foo");
// returns null

localStorage.setItem("foo", "bar");
// returns undefined

localStorage.getItem("foo");
// returns "bar"
```

It's as easy as that! A quick example using session storage:
```javascript
sessionStorage.setItem("foo", "bar");
// returns undefined

sessionStorage.getItem("foo");
// returns "bar"

// *Tab gets closed. Another tab with the same URL gets loaded*

sessionStorage.getItem("foo");
// returns null
```

And that's basically it. It's very easy and very helpful! For more detail, please [read the documentation](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API).
