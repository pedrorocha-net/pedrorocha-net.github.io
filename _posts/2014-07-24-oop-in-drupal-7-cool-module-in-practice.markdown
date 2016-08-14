---
layout: post
title:  "OOP in Drupal 7: Cool module in practice"
date:   2014-07-24 00:00:00 -0300
---
Hey, do you wanna know how to:

*   reduce the amount of code needed to create modules
*   turns the code more readable
*   make it easier to find bugs
*   make it easier to change business logic
*   make it easier to improve code

Sounds good, right? If you only wanna know about code, [jump to here](#code), or read about the historical background of the module ;)

## Module background

Drupal community is talking a lot about OOP in the last months, because Drupal 8 is bringing sanity to developers, but OOP is not being used on Drupal 7 only because it's not being used. Sounds weird, but it is true: the tools are already here to help us develop modules that are easier to understand, contribute and maintain.

I came in a moment that i thought "wow, my Drupal code could really become more organized", and this was because i didn't agree to have .module and .inc files with dozens of functions that, in most of the time, doesn't relate to each other: they were just there, everyone in the same bag, because it's a common practive among contrib modules. Maybe an .admin.inc file, but nothing more than this.

Yes, Drupal was created in a PHP without OO, but nothing stops us from use these resources in the last years, since PHP 5, so it's just a question of "bad practice". For me, as i worked with J2EE for 3 year, before jumping into Drupal, in 2010, the last years i fell that my code was becoming worst, in terms of reuse and readability.

[Entity module](https://drupal.org/project/entity) was a great friend in this jorney and when i knew [X Autoload](https://drupal.org/project/xautoload)(that makes Drupal 7 understand PSR-0 - already bundled with Drupal 8), an idea came to mind: OOPify Drupal. And i'm not talking about create classes and need to register in some kind of registry: i wanna create a class and it simply works. Clear the cache is all i should need.

After around 1 year working in some projects and testing some approachs, i started to create the [Cool module](https://drupal.org/project/cool), aiming to create an OOP wrapper to the Drupal API, allowing me to do commons things, like create a Page in hook_menu(), a block in hook_block(), and handle a Form, with classes. In other words, i wanna see classes sharing methods when it makes sense, and leaving other methods private when it only makes sense internally. It doens't make sense to keep every one of these methods as functions in the same .module file.

## "Show me the code"

Currently, [Cool module](https://www.drupal.org/project/cool) provides wrappers to the following drupal components:

*   hook_menu - create pages(menu routes)
*   hook_block - create blocks(with configuration forms, submit, etc, inside the class)
*   forms - bundle the form definition, validate and submit rules inside 1 class

As an example, to create a page route(hook_menu), all you need to do is:

*   create you custom module with dependency of "cool"(that depends on "xautoload")
*   create a folder following the PSR-0 pattern, "lib/Drupal/[your_module]"
*   create a folder named "PageControllers" anywhere inside the previous folder(you can place on the root created, but you are free to create inside other folders too, like "lib/Drupal/[your_module]/Controllers/PageControllers"
*   create you class, like "MyPage.php"(remember that it's .php, not .inc), implementing "\Drupal\cool\Controllers\PageController" and it's methods (see the gist above)
*   clear the cache

To more details on every options, you can take a look at the "cool_examples" submodule.

<script src="https://gist.github.com/pedrorocha-net/4ebbb7a6d8cf30e6c031.js"></script>