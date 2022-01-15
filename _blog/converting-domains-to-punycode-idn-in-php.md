---
layout: post
title:  "Converting Domains to Punycode/IDN (and vice versa) in PHP"
date:   2022-01-15 18:00:15 +0200
tags: ["php"]
---

So you are building an application which has some relation to domains. Everything works fine and one day a user with the domain `reisebüro.de` comes along, something breaks, 
new ticket created, and now you're trying to deal with the issue.

Fear not: Punycode!

The world is complex and there are a lot of language which don't comply with ASCII. So there is Punycode to enable representation of non ASCII complying text in ASCII. PHP has two helpful internal functions `idn_to_ascii` and `idn_to_utf8` which help us convert a non ASCII complying domain name, as `reisebüro.de`, to a working ASCII compliant version.

To convert a non ASCII compliant domain to ASCII use `idn_to_ascii`. For example:
```php
$domain = 'reisebüro.de';
$asciiDomain = idn_to_ascii($domain);
var_dump($asciiDomain);
```
Output:
```text
string(19) "xn--reisebro-c6a.de"
```
Very easy!

If you would like to convert this domain back from Punycode, use `idn_to_utf8`. For example:
```php
$domain = 'xn--reisebro-c6a.de';
$utf8Domain = idn_to_utf8($domain);
var_dump($utf8Domain);
```
Output:
```text
string(13) "reisebüro.de"
```
And that's it! Very easy, very reliable. However, there are some cases were `idn_to_ascii` and `idn_to_utf8` will fail. So take care of error handling.
