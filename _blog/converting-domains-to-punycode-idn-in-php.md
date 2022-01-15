---
layout: post
title:  "Converting Domains to Punycode/IDN (and vice versa) in PHP"
date:   2022-01-15 18:00:15 +0200
tags: ["php"]
---

So you are building an application which has some relation to domains. Everything works fine and one day a user with the domain `reisebüro.de` comes along, something breaks, 
new ticket created, and now you're trying to deal with the issue.

Fear not: Punycode!

