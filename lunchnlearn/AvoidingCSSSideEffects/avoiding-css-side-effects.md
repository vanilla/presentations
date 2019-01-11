## Avoiding side effects while writing HTML & CSS
![](https://camo.githubusercontent.com/48ff1042fdbc3d66230d4cf00d3e305ec41b3b85/68747470733a2f2f74697073792e6769746875622e696f2f627562626c792d62672f627562626c792e676966)

--------------

##What do you mean by "side effects"?

I mean trying to fix one thing and breaking another.

![inline](https://media.giphy.com/media/13XW2MJE0XCoM0/giphy.gif)

----------

# Or... to put it in a different way

###Two CSS properties walk into a bar.
### A barstool in a completely different bar falls over.

----



# Part 1: Theory

There are many, methodologies/frameworks for writing good modular CSS. [*SMACSS*](https://smacss.com/), [*Atomic Design*](http://atomicdesign.bradfrost.com/chapter-2/), [*SUIT CSS*](https://suitcss.github.io/) and [*BEM*](http://getbem.com/introduction/) are some of the most popular.

At Vanilla, we have our own flavour, but they're all pretty similar at their core. This talk won't into all the differences , but focus on the higher level concepts.

-------------

# The core of the problem: __*SCOPE*__

Scoping is a big problem in CSS. It's very difficult to detect any side effects when you make a modifaction to styles. 

Even if you do a proper search through their whole project, there might be pockets, customize theme or plugins that get added later that may interfere with your styles.

________

# __*BAD*__ selectors

```css
a { ... }
.Title { ... }
.Row { ... }
```

These are so generic, they are used in a ton of different places in Vanilla and are almost guarenteed to cause problems.

---------

# __*BAD*__ classes

In Vanilla, the class `.Discussions` is used both on the `body` tag AND on the `li` of containing the link to the discussions page.

This is very unintuitive and means that using just the single class is **never enough** to only target one!

______________________

# Scoping your styles to a "component"

(Note different methodologies call these **components**, **modules**, **blocks**, etc. The idea remains the same, it's one "chunk")

Let's take this simple component as an example.

-------

 ![inline](/Users/stephanelafleche/Documents/vagrant-vanilla/git_repos/presentations/lunchnlearn/AvoidingCSSSideEffects/ExampleComponent.png) 

--------


```html
<nav class="categoriesNav">
	<h2 class="categoriesNav-title">
		Categories
	</h2>
	<ul class="categoriesNav-items">
		<li class="categoriesNav-item">
			<a href="#" class="categoriesNav-link">
				All Categories
			</a>
			<span class="categoriesNav-count">
				22.3K
			</span>
		</li>
        <!-- Repeat for each item -->
	</ul>
</nav>
```

---

- We give one name to the root of the component

- Children elements are prefixed with the parent name

- Each class is unique and there's no ambiguity here

- Will generate "flat" style sheet 

--------

```css
.categoriesNav{ ... }
.categoriesNav-title{ ... }
.categoriesNav-items{ ... }
.categoriesNav-item{ ... }
.categoriesNav-link{ ... }
.categoriesNav-count{ ... }
```

No crazy nesting for selectors!

Unique classes for each element!

Since we're not styling base elements, we can even swap out the HTML elements without difficulty.

--------------



![inline](/Users/stephanelafleche/Documents/vagrant-vanilla/git_repos/presentations/lunchnlearn/AvoidingCSSSideEffects/ExampleComponent_full.png)

----------------


# Managing scope (pt 1)

* Your selector should only apply to one region and not "bleed" out
* Avoid super generic classes that are likely to be used like "header" when in a project with a lot of legacy code. **Especially in Vanilla, since we have plugins, pockets, and all kinds of client customizations**

---------

# Managing scope (pt 2)

* Don't style on base elements (except on a reset/normalize type sheet)
* Make classes! Classes are usually your best option rather than IDs or elements
* Be very unimaginative with your names

------

# Managing scope (pt 3)

* Ideally, your style partial has the same name as the component you've made (example, all our "categoriesNav" styles are in a file called "categoriesNav")
* If your component is too complex, you should probably break it down to multiple

------

## Mixing multiples classes are ok, but be careful

You can mix and match classes, but be careful it can get messy and difficult to understand what each class is supposed to do.  That's when it's difficult to predict "side effects" of modifying either of those classes for other components.

------

## State

In Vanilla, we use the SMACSS style "is" or "has" prefixes for states. Example: "isActive"). These state classes are meant to not be used alone, but with another class.

```
.categoriesNav-item.isActive { ... }
```

--------

# Global scoped styles (pt 1)

If you have a really generic global class, like `.button` it's extreamly difficult to be sure modifying won't break anything else. It's also much harder to "undo" styles than to just start fresh. A "flater" stylesheet is much easiser to understand and to maintain. 

--------

# Global scoped styles (pt 2)

Make sure the purpose of those shared class is well defined and clear. If you find yourself writing a exceptions, consider making another class.

----------

# Part 2: The Real World

That's all fine and good, but we don't always have the luxury of rewriting all the HTML/CSS.

Use the **simplest** selector that __*specifically*__ targets what you want.

--------

#[fit]Somtimes, ugly is necessary
------------


Example: 
```
body.Section-SearchResults .AdvancedSearch .P.Buttons { ... }
```

A. `body.Section-SearchResults`

If this is only for one page, we need to use a page class. Note we protect ourselves to not mistake any other element with the same class name by using the `body` in the selector

--------
Example:
```
body.Section-SearchResults .AdvancedSearch .P.Buttons { ... }
```

B. `.AdvancedSearch`

If buttons are on multiple places in the page we need to specify which ones we want to target.

--------

Example: 
```
body.Section-SearchResults .AdvancedSearch .P.Buttons { ... }
```

C. `.P.Buttons`

The extra `.P` here is here to bump up the specificity because we want to overwrite some times.

___________

# Note

It's generally much easier to create a new class than to undo styles from an existing class. It's also much easiser to know what will happen if you add a new class, vs modifying an exiting one.

---
## Further Reading

* https://css-tricks.com/regarding-css-global-scope/ 
* https://smacss.com/
* http://atomicdesign.bradfrost.com/chapter-2/
* https://suitcss.github.io/
* http://getbem.com/introduction/

-----------

## Questions

![](https://media.giphy.com/media/xUOxfjsW9fWPqEWouI/giphy.gif)