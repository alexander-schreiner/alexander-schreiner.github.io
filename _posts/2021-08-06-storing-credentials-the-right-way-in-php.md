---
layout: post
title:  "Storing credentials the right way in PHP"
date:   2021-08-06 12:30:15 +0200
categories: [php]
---

Almost all applications have some sort of secrets, credentials or password which must remain secret and kept private. Even though storing credentials is such an essential part of 
modern software development, you still see live applications storing their credentials in raw code and even having them checked into their version control. Even well known 
references like [PHP: The Right Way](https://phptherightway.com/#:~:text=%24link%20%3D%20new%20PDO(%0A%20%20%20%20%27mysql%3Ahost%3Dyour-hostname%3Bdbname%3Dyour-db%3Bcharset%3Dutf8mb4%27%2C%0A%20%20%20%20%27your-username%27%2C%0A%20%20%20%20%27your-password%27%2C%0A%20%20%20%20array(%0A%20%20%20%20%20%20%20%20PDO%3A%3AATTR_ERRMODE%20%3D%3E%20PDO%3A%3AERRMODE_EXCEPTION%2C%0A%20%20%20%20%20%20%20%20PDO%3A%3AATTR_PERSISTENT%20%3D%3E%20false%0A%20%20%20%20)%0A)%3B)
have made the mistake of writing credentials as literal strings in code (yes, i know it's only an example snippet, but people use this website as a best practice coding guide, which
will lead them to copy this behavior).


```php
// snippet
```
