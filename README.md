# PHP Assumptions
**This project is a fixed drop-in replacement for [rskuipers/php-assumptions](https://github.com/rskuipers/php-assumptions)**

> [!NOTE]  
> PHP 8.x compatibility is WIP.

## Setup
```sh
$ composer require --dev johnatas-x/php-assumptions
```

## Introduction
PHP Assumptions is the result of a proof of concept inspired by the "[From assumptions to assertions](http://rskuipers.com/entry/from-assumptions-to-assertions)" blog post.
It's a static code analysis tool doing checks for weak assumptions.

This is an example of an **assumption**:

```php
if ($user !== null) {
    $user->logout();
}
```

Running `bin/phpa` on this file would yield the following output:

```
----------------------------------------------
| file        | line | message               |
==============================================
| example.php | 3    | if ($user !== null) { |
----------------------------------------------

1 out of 1 boolean expressions are assumptions (100%)
```

This is an example of an **assertion**:

```php
if ($user instanceof User) {
    $user->logout();
}
```

## Tests
This project is built with [PHPUnit](https://github.com/sebastianbergmann/phpunit) and [Prophecy](https://github.com/phpspec/prophecy-phpunit).
In order to run these tests make sure you have dev dependencies installed with composer.

Running PHPUnit:
```sh
$ ./vendor/bin/phpunit
```
