---
layout: post
title:  "Storing credentials the right way in PHP"
date:   2021-08-06 12:30:15 +0200
categories: [php][security]
---

Almost all applications have some sort of secrets, credentials or passwords which must remain a secret and kept private. Even though storing credentials is such an essential part of modern software development, you still see live applications storing their credentials in raw code and even having them checked into their version control. Even well known 
references like [PHP: The Right Way](https://phptherightway.com/#:~:text=%24link%20%3D%20new%20PDO(%0A%20%20%20%20%27mysql%3Ahost%3Dyour-hostname%3Bdbname%3Dyour-db%3Bcharset%3Dutf8mb4%27%2C%0A%20%20%20%20%27your-username%27%2C%0A%20%20%20%20%27your-password%27%2C%0A%20%20%20%20array(%0A%20%20%20%20%20%20%20%20PDO%3A%3AATTR_ERRMODE%20%3D%3E%20PDO%3A%3AERRMODE_EXCEPTION%2C%0A%20%20%20%20%20%20%20%20PDO%3A%3AATTR_PERSISTENT%20%3D%3E%20false%0A%20%20%20%20)%0A)%3B)
have made the mistake of writing credentials as literal strings in code (yes, i know it's only an example snippet, but people use this website as a best practice coding guide, which will lead them to copy this behavior).

## How to do it right

Store your credentials in an .env file at your project root. Your project root, or repository root, will be at the directory level on which your composer.json or README.md will be typically located at. Once you created your .env file, you will have to migrate your credentials to the following structure:

```text
SOME_KEY=somesecret
```

If you need an example to learn by, take a look at this example .env from [The Laravel Framework](https://github.com/laravel/laravel/blob/8.x/.env.example).

Please make sure, that your .env file is not checked into your version control. If you are using Git, you will have to add .env to your .gitignore. The .gitignore file will also be located at the root of your project (For more information on .gitignore, [Read the documentation](https://git-scm.com/docs/gitignore)). Also [check out this example](https://github.com/laravel/laravel/blob/8.x/.gitignore#L6).

Now we will be looking at how to actually use the values stored in .env in our php code. For this, we will be using a library called [vlucas/phpdotenv](https://packagist.org/packages/vlucas/phpdotenv). 

Require the library into your project by running ```composer require vlucas/phpdotenv```. If you are not familiar with Composer, [get started here](https://getcomposer.org/doc/00-intro.md)).

After installing the library, you will need to load the .env variables into your application:

```php
$dotenv = Dotenv\Dotenv::createImmutable(__DIR__);
$dotenv->load();
```

This piece of code is best placed in the bootstrapping of your application, since you will most likely require values from .env in every single request. Depending on your php application, there might be some standard way to this.

After loading your .env variables, you may simply use them:

```php
$someThing = $_ENV['SOME_KEY'];
```

If you want to beautify your code, by not calling a [super global variable](https://www.php.net/manual/en/reserved.variables.environment.php) all the time, you should take
a look at [creating your own helper functions](https://tutsforweb.com/creating-helpers-laravel/).
