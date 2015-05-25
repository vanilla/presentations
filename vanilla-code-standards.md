footer: © 2015 Vanilla Forums
slidenumbers: true

# [fit] Vanilla Coding Standards

### [fit] Some things you need to know about writing code at Vanilla Forums

---

# Contents

1. Coding standards
2. Grammar
3. Tools
4. Transitioning

---

# [fit] 1

### Coding standards are about spacing, punctuation, variable & function naming in source code.

---

# Coding Standards

* Use [PSR-1](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md) and [PSR-2](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md) standards.
* Opening curly braces go on the same line (hail Lord Brackos).
  
  ```php
  if ($probably === true) {
  ```  
  
* Don't put a space on either side of string concatenation dots.


  ```php
  echo "It's ".date('r')." today.\n"
  ```

---

# Function Naming

*The PSRs don’t include any rules regarding naming.*

* We're talking about _functions_, not _methods_.
* Functions should generally use `camelCase()`.
* Functions that add to a family of built in php functions should follow that naming scheme (ex. `str_begins()`, `array_translate()`).
* Functions that aren't complete words are okay (ex. `val()`, `config()`).
* Try and make functions one word.

---

# [fit] 2

### [fit] Grammar is important because coders don't just write code.

---

# Grammar

Even though we mostly write code, there are a wide range of places where writing skills are important: documentation, emails, blog posts, etc. **Coders don't just write code.**

Use proper grammar at all times. Write in complete sentences. Communication may be your most important career skill.

---

# Docblock Summaries

Write summaries in the *imperative mood*. This means write as if giving a command or instruction.

```php
/**
 * Make sure the current request is against HTTPS.
 */
function forceSSL() {
    // ...
}
```

Hint: Don't pluralize that verb!

---

# @param

Docblock parameters usually start with "the". Boolean parameters often start with "Whether or not".

```php
/**
 * Shuffle the elements of an array.
 * @param array $array The array to shuffle.
 * @param bool $preserveKeys Whether or not to preserve key/values…
 */
function array_shuffle(&$array, $preserveKeys = false) {
    // ...
}
```

---

# @return and @throws

Start `@return` sentences with the word "Returns".

```php
/**
 * Return the current Unix timestamp.
 * @return Returns the current time measured in the number of seconds since the Unix Epoch (January 1 1970 00:00:00 UTC).
 */
function now() {
```

Start '@throws` with "Throws an exception when…".

```php
/**
 * Get the command command line arguments.
 * @throws Exception Throws an exception when not called from a command line context.
 */
function getCliArgs() {
```
---

# Docblock Tips

* Use Markdown for basic formatting.
* Use the `{@link}` tag to link to other documentation.

```php
/**
 * Make sure that a directory exists.
 * @param string $dir The name of the directory.
 * @param int $mode The file permissions on the folder if it's created.
 * @throws Exception Throws an exception when {@link $dir} is a file.
 */
function touchdir($dir, $mode = 0777) {
    // ...
}
```

---

# Writing Comments

* Full line comments use complete sentences, including punctuation.
* End of line comments are just a few words and aren't sentences.

```php
// This is a full line comment and should be a complete sentence.
$foo = 'bar'; // eol note
```

---

# Commit Messages

* Comments aren't the place to be verbose. That's where commit messages come in.

* When committing changes to an addon, make sure the name of the addon is in the subject of the commit message.

* Pull requests should have a subject and a body.

* See [How to Write a Git Commit Message](http://chris.beams.io/posts/git-commit/) for a great guide on commit messages.

---

# The 7 Rules of Commit Messages

1. Separate subject from body with a blank line.
2. Limit the subject line to 50 characters.
3. Capitalize the subject line.
4. Do not end the subject line with a period.
5. Use the imperative mood in the subject line.
6. Wrap the body at 72 characters.
7. Use the body to explain what and why vs. how.

---

# [fit] 3

### [fit] Some helpful tools to ~~force~~ help you write standard code.

---

# Tools

* The **.editorconfig** file makes sure spacing and end of lines are correct within a project.

* **phpcs** will check your code for code standard errors. Vanilla's code standards can be found at [addons/standards/Vanilla](https://github.com/vanilla/addons/tree/master/standards/Vanilla).

* PhpStorm has support for both .editorconfig and phpcs.

---

# [fit] 4

# [fit] Transitioning

## [fit] You might have noticed that Vanilla does not adhere to these code standards *yet*.

---

# Convert Vanilla to Four Spaces

* Get as many pull requests merged by Wednesday, May 27 EOD.

* On Thursday, May 28 morning convert to 4 spaces.

* The commits will be on a subdirectory-by-subdirectory basis.

* Even though we have automated tools for code formatting, the changes must be reviewed. Those with Kaleidescope can do this.

---

# Convert Vanilla to Correct Case

* Camel case all the methods in `/library`.

* Correct case functions in `/library`.

* Correct stuff like `TRUE` to `true` in `/library`.

* Applications and plugins can be done later. Make some pull requests!

* Properties can't be camel cased without breaking BC. Use camel casing moving forward and we can fix core classes with pull requests.

^ This shouldn't cause any bugs, but might so we need to be careful and pulling as a team before deploy.

^ We should be moving to get/set functions in properties, but need core support.

---

# Moving Forward

* Learn our coding standards.

* Use the correct standards moving forward.

* Only correct standards alongside other pull requests if it's not too disruptive.

* If you're bored, make a pull request to correct the standards in a file or two.

---

# Finally, Why Bother?

*Converting Vanilla's coding standards has some downsides and no functionality improvements. So why bother?*

* Better interoperability with other PHP projects.

* We want the code we look at every day to look beautiful.

^ Converting Vanilla's coding standards is a big job with many downsides and no functionality improvements. Why even bother with this change?

^ *One of the core principals of Vanilla's culture is that our developers are craftspeople. We strive to create the best software and part of that process involves a sense of aesthetic. We want to have an aesthetic experience with the stuff we look at every day: our very source code.*

---

# [fit] Fin

### ...and questions