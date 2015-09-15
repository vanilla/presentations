footer: © 2015 Vanilla Forums
slidenumbers: true

# [fit] Vanilla Internals

### [fit] How requests are handled within Vanilla

---

# How most Vanilla programmers develop

* Write some controller methods.
* Write some views.
* Write plugins and event handlers.

But how are these things wired together?

---

# First, some core PHP principals

* *PHP doesn't have any concept of shared memory.* Every request has to set up its environment, read configs, etc. from scratch.
* *PHP doesn't have any concept of multi-threading.* Every request can be followed from start to finish in a single line.

Both of these points mean there isn't really any magic happening in a PHP script.

---

# Everything starts in index.php

Every request within Vanilla goes through `index.php` and does two main things:

1. **Bootstrap**. Initialize the framework and make all objects and functions available.
2. **Dispatch**. Dispatch the current request to the appropriate controller method.

---

# [fit] 1

## [fit] Bootstrap

### [fit] The bootstrap sets up the framework

---

# In the bootstrap

* Include core functions and our *autoloader*.
* Load the default and app *configuration*.
* Initialize *Gdn::Request()* from superglobals.
* Initialize *addon managers*.
* Load the current *locale*.
* Initialize the current user *session*.
* Include non-core functions.

---

# The autoloader

In PHP, autoloaders are functions that are registered and called whenever PHP can't find a class.

* Vanilla's autoloader is in *Gdn_Autoloader*.
* Our autoloader crawls the `/library` directory by default.
* Once the enabled addons are known their directories are added and take precedence.

All class to file mappings get lazy cached in `/cache`.

---

# Configuration files

By default, configuration information is stored in PHP files as big, nested arrays.

* Vanilla loads/saves configurations in *Gdn_Configuration*.
* The configuration must be loaded early so we know were the database & cache are, what addons are enabled etc.
* Configurations are loaded once, but can be updated on settings pages.

---

# The Gdn_Request class

* Vanilla stores HTTP request data in *Gdn_Request*.
* Gdn::Request() points to the request for the current page.
* Gdn_Request gets its data from `$_SERVER`, `$_GET`, and `$_POST`.
* The request class works with custom .htaccess or nginx configurations to support nice urls.

---

# The addon managers

Each addon type (application, theme, plugin) has a manager object. They are mostly the same.

* They store the currently enabled addons.
* They have functions to enable/disable addons.
* The `Gdn_PluginManager` contains all event handling logic.

---

# The locale

All of the translations for each locale are stored in PHP arrays. They are sort of like configurations.

* The *Gdn_Locale* class is like an addon manager for locales. It loads all of the locales for the currently enabled addons and locale packs.
* Locale load order: applications, locales, plugins, themes, then config.
* Each time a locale file is loaded it overwrites any duplicate keys from before.

---

# The session

The session represents the current user in Vanilla. It makes information about that user as well as their permissions available to the application.

* The *Gdn_Session* class handles the session.
* The ID of the session'd user is stored in the cookie. It's secured with HMAC SHA1.
* The cookie's signature is verified then the user and permissions are loaded.

---

# That's the bootstrap!

At this point everything that needs to be loaded is loaded and is now available for use.

---

# [fit] 2

## [fit] Dispatch

## [fit] The dispatcher routes the requests to controller methods

---

# What happens in a dispatch?

The dispatch is handled by *Gdn::Dispatch()->Dispatch()*.

* Check to see if any URLs have been overridden with *routes*.
* Find a *controller* that satisfies the path.
* Check to see if a plugin overrides the controller.
* Initialize the Controller
* Call the method.

---

# Overriding URLs with routes

In Vanilla, routes are regular expressions that map one URL to another URL.

* Routes are handled in the *Gdn_Route* class.
* There are some core routes like `Default404 => /home/notfound` for page not found errors.
* Used to map URLs from imports to our URLs.

When dispatching, if a route matches then we continue dispatching against the mapped URL.

---

# Finding controllers

* Controllers are found by analyzing the path of the URL.
* Both */controller/method* and */application/controller/method* can be used.
* To find a controller we just use `class_exists()` and the autoloader takes over to look up the controller﹡

﹡It's not this easy, but that's the basics.

---

# Initializing the Controller

You can't just instantiate a controller and call a method.

* Assign the name of the current URL and method to controller properties.
* Call `Gdn_Controller->init()`.
* Instantiate properties from `Gdn_Controller->uses`.

---

# Calling controller methods

* Check to see if there is an event that overrides the controller method. If so, use it instead.
* Reflect the parameters on the method.
* Call the controller's method with `call_user_func_array()`.

---

# Other uses for the dispatcher

* The dispatcher handles exceptions thrown from controllers.
* The dispatcher handles maintenance mode.
* The dispatcher handles private communities.
* Most of these other users just involve just dispatching to a different controller!

---

# That's the dispatcher!

Once the dispatcher calls the controller's method it's job is basically done and the controller completely takes over.

Inside the controller is where most Vanilla developers live.

---

# [fit] die

[https://github.com/vanilla/presentations/blob/master/vanilla-internals.md](https://github.com/vanilla/presentations/blob/master/vanilla-internals.md)