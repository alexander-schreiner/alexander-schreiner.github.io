---
layout: post
title:  "Creating your own helpers functions in PHP (Framework agnostic)"
date:   2021-07-13 08:30:15 +0200
categories: [php]
---

Helper functions are a great way to beautify your code. Some PHP Frameworks even ship with [their own built-in helpers](https://laravel.com/docs/8.x/helpers). Start here to create your own helper functions, but, unlike other tutorials, 100% Framework agnostic.

## Creating your file
At first, you'll need to create a new PHP file, for the sake of this tutorial we will call our helper functions file `helpers.php`. But in advance, you need to choose where to place your file in your project structure. Since we are on a Framework agnostic tutorial i can't give you a specific answer, but generally speaking: The file will be accessible to all of your code through autoloading, therefore you should place it in a generalized place, such as `src/helpers.php` or alike.

## Autoloading
After having created your file we will use [Autoloading](https://www.php.net/manual/en/language.oop5.autoload.php) to make your functions available. Open your `composer.json` file at the root of your project. Now you should locate the [autoload block](https://getcomposer.org/doc/04-schema.md#autoload), if you can't find it, just create it. Inside the autoload block locate [`files`](https://getcomposer.org/doc/04-schema.md#files). Thereafter, add your newly created `helpers.php` file to the `files` block inside `autoload`. Your autoload block should now look something like this:

```json
"autoload": {
    "files": [
        "src/helpers.php"
    ],
    "psr-4": {
        "App\\": "app/"
    }
}
```

After adding your `helpers.php` to your `composer.json` we will now [dump the autoloader](https://getcomposer.org/doc/03-cli.md#dump-autoload-dumpautoload-). Now, on every request, your new `helpers.php` file will be loaded automatically.

## Adding functions
Now we are ready to define helper functions in our `helpers.php` file. For example:

```php
<?php

if (! function_exists('redirect')) {
    function redirect(string $url) {
        // (...)
    }
}
```

And finally, you may use your helper functions the following way:

```php
// (...)

    public function proccess(): void
    {
        // (...)
        if ($shouldRedirect === true) {
            redirect($secureUrl);
        }
    }

// (...)
```

Be aware not to bloat your `helpers.php` since it will be loaded at every request.
