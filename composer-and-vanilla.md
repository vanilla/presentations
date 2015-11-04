# [fit] Vanilla and Composer
## [fit] An overview of Vanilla's Composer Integration Plans

---

# What is Composer?

* *Dependency manager for PHP.*
* Allows you to include other PHP projects as dependancies.
* Makes your PHP project available as a dependency to other projects.
* Provides a nice autoloader.

---

# Benefits of Composer

* Allows you to more easily use *third-party code*.
* Allows your project to *separate development and production* functionality.
* Allows you to *split a large codebase* into separate independent libraries.
* Once you've isolated your code you have a better idea of *testability*.

---

# Getting Started With Composer

* Install composer: `brew install composer`
* Put a `composer.json` in the root of your PHP project.
* Include `vendor/autoload.php` to use Composer's autoloader.
* Run `composer install`.
* Optionally, Submit your project to [packagist.org](https://packagist.org/).
* Run `composer update` to update dependencies to newer versions.

---

# A Sample composer.json

```json
{
    "name": "vanilla/mustacher",
    "description": "Run mustache templates against a JSON file from the command line.",
    "minimum-stability": "stable",
    "license": "MIT",
    "authors": [
        {
            "name": "Todd Burry",
            "email": "todd@vanillaforums.com"
        }
    ],
    "require": {
        "vanilla/garden-cli": "~1.3", // names of other composer libraries
        "mustache/mustache": "~2.9"
    },
    "autoload": {
        "psr-4": {
            "Mustacher\\": "src" // where class files of this project are
        }
    },
    "bin": [
        "bin/mustacher" // custom CLI bin
    ]
}
```

---

# Other Useful composer.json Keys

* *requre-dev*, *autoload-dev*: Add dependencies and objects for use only when developing.
* *repositories*: Point to dependencies that aren't on [packagist.org](https://packagist.org/).

```json
"repositories": [
    {
        "type": "vcs",
        "url": "git@github.com:vanilla/garden.git"
    },
    ...
]
```

---

# The composer.lock File

* When running `composer install/update` a *composer.lock* file is generated.
* This file includes exact git hashes of all your projects dependencies. This can help ensure all developers are using the same dependencies.
* Commit the composer.lock file for *projects*.
* *Don't* commit the composer.lock file for *libraries*.

---

# How Will Vanilla use Composer?

* Composer will be Vanilla's core library autoloader (not add-ons).
* The hard-included third-party vendor libraries will slowly move to composer dependencies.
* We'll develop some smaller libraries separately instead of with Vanilla.
* Include separate libraries as though they are core for different versions of Vanilla.

---

# Implementing Composer

* Replace the core auto-loader with composer. (in [PR](https://github.com/vanilla/vanilla/pull/2676))
* Create a build process for Vanilla using Phing. (done)
* Create a way to add composer dependencies locally. (in [development](https://github.com/vanilla/vanilla/tree/feature/composer-local))
* Move the /vendors dependencies into composer dependencies one-by-one. (todo carefully)

---

# Vanilla (The Company) Already Uses Composer

We've already developed some projects & libraries using composer.

* [Garden CLI](https://github.com/vanilla/garden-cli): A command line parser for developing CLI applications.
* [Garden HTTP](https://github.com/vanilla/garden-http): An unbloated HTTP client library for building RESTful API clients.
* [Mustacher](https://github.com/vanilla/mustacher): Run mustache templates against a JSON file from the command line.