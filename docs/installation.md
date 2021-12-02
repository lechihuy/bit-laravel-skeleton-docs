---
sidebar_position: 2
---

# Installation

> Because the package hasn't released yet, you can only install it via Git clone.

First, clone this repository at top-level directory of your Laravel project.
```shell
git clone https://github.com/lechihuy/bit-laravel-skeleton
```

The directory structure of your project belike
```
app
bootstrap
bit-laravel-skeleton
config
...
```

Then, open your `composer.json` file and add several the following code
```json title="composer.json"
"require": {
    "lechihuy/bit-laravel-skeleton": "@dev"
},

"repositories": {
    "bit-laravel-skeleton": {
        "type": "path",
        "url": "./bit-laravel-skeleton"
    }
}
```

Finally, run the following command in your terminal
```shell
composer update
```
