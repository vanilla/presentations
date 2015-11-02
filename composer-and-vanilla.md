# [fit] Vanilla and Composer
## [fit] An overview of Vanilla's Composer Integration Plans

---

# What is Composer?

* Dependency manager for PHP.
* Allows you to include other PHP projects as dependancies.
* Makes your PHP project available as a dependency to other projects.
* Provides a nice autoloader for your PHP project.

---

# Getting Started With Composer

* Install composer: `brew install composer`
* Put a `composer.json` in the root of your PHP project.
* Include `vendor/autoload.php` to use Composer's autoloader.
* Run `composer install`.

---

# A Sample composer.json

```json
{
	"name": "vanilla/garden-cli",
	"description": "A command line parser for your next php cli script.",
	"license": "MIT",
	"authors": [
		{
			"name": "Todd Burry",
			"email": "todd@vanillaforums.com"
		}
	],
	"require": {
		"php": ">=5.4.0"
	},
	"autoload": {
		"psr-4": {
			"Garden\\Cli\\": "src"
		}
	}
}
```

---

# How Will Vanilla use Composer?

* Composer will be Vanilla's core library autoloader (not add-ons).
* The hard-included vendor files will slowly move to composer dependencies.
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

We've already developed some libraries using composer.

* [Garden CLI](https://github.com/vanilla/garden-cli): A command line parser for developing CLI applications.
* [Garden HTTP](https://github.com/vanilla/garden-http): An unbloated HTTP client library for building RESTful API clients.
* [Mustacher](https://github.com/vanilla/mustacher): Run mustache templates against a JSON file from the command line.