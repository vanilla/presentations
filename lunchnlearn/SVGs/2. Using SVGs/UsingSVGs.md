# The _many_ and **exciting** ways to include _*SVGs*_ in your HTML page

![](https://cdn.dribbble.com/users/910669/screenshots/2248501/moon2.gif)

---
## As Image

```html
<img src="./media/Firefox_Logo.svg" alt="FireFox"/>
```

| Pros                        | Cons                  |
| --------------------------- | --------------------- |
| Easy!                       | Can't animate         |
| Stored in the browser cache | Can't change contents |



---
## As background

```css
 background: url(./media/Firefox_Logo.svg);
```

| Pros                                                         | Cons                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Behaves like regular image backgrounds                       | Can't animate                                                |
| Can be base 64 encoded and put in a SASS mixin to have various colours | Can't change change contents with CSS (except for some browsers supporting background transitions) |
| Stored in the browser cache                                  |                                                              |

---
## As font

Since browser support for custom fonts is good, some people had the idea to use a font for custom icons. 

The most famous example is: https://fontawesome.com/

---

## As font

**Vanilla uses this for theming:**
https://github.com/vanilla/font-vanillicon

**Generate your own font (command line)**
https://github.com/FontCustom/fontcustom

**Generate your own font (uploading files online):**
https://icomoon.io/app/#/select/font

---

## As font

| Pros                                                      | Cons                                                       |
| --------------------------------------------------------- | ---------------------------------------------------------- |
| Easy to use once the font is generated                    | You need to generate the font every time you make a change |
| You can use font animations and styles (like text shadow) | Can't have multiple colours                                |
| Stored in the browser cache                               | Can't change contents with CSS                             |

---
## As "sprite" sheet

We have have one master "sprite" SVG and then use parts of it elsewhere. The result is kind of like the old school sprite icon sheets. But instead of cropping an image, you're cloning part of an SVG into another spot with the `<use/>` tag.

1 - We start with our SVG

```html
<svg id="icon-1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
	<polygon fill="currentColor" points="14 11 14 25 26 18"/>
</svg>
```

---
## As "sprite" sheet 

2 - Just change `svg` tag for `symbol` and put it in the sprite SVG with an ID.

```html
<svg style="display: none;">
    <!-- First Icon -->
	<symbol id="icon-1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
      <polygon fill="currentColor" points="14 11 14 25 26 18"/>
    </symbol>
     <!-- Second Icon -->
    <symbol id="icon-2" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
      <polygon fill="currentColor" points="14 11 14 25 26 18"/>
    </symbol>
    <!-- You can add as many as you like -->
</svg>
```
---
## As "sprite" sheet 

Make SVG tags where you need them, add a `<use/>` tag and reference the ID of the icon you want. Can be styled, but not the components of the icon.

You can, however, compose them together and target  `<use/>` in CSS.

```html
<svg class="myCoolIcon1">
  <use xlink:href="#icon-1" />
</svg>

<!-- Compose them together! -->
<svg class="myCoolIcon2">
  <use xlink:href="#icon-1" />
  <use xlink:href="#icon-2" />
</svg>
```

---
## As "sprite" sheet

| Pros                                                         | Cons                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Easy to update                                               | Hard to manage in large projects (how many can we load)      |
| Icons used in lots of places don't need the full code redeclared each time | Doesn't cache                                                |
|                                                              | You are either loading your whole sprite sheet each page load or you need to manage it yourself. |



---
## Inline

Put it straight in your HTML

```html
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
	<polygon class="partA" fill="currentColor" points="14 11 14 25 26 18"/>
    <polygon class="partB" fill="currentColor" points="14 11 14 25 26 18"/>
</svg>

```

| Pros                                     | Cons                                                   |
| ---------------------------------------- | ------------------------------------------------------ |
| Easy to use                              | More HTML                                              |
| Can target any parts of the SVG with CSS | Does not cache                                         |
|                                          | Not practical for large projects unless using tempates |



---
## React Component

`vanilla/library/src/scripts/components/icons`

```jsx
export function expandAll(className?: string) {
    const title = t("Expand All");
    return (
        <svg
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 24 24"
            className={classNames("icon", "revisionIcon", "revisionIcon-revision", className)}
            role="img"
            aria-label={title}
        >
            <title>{title}</title>
            <path d="M8,5H22V7H8ZM8,9H22v1.5H8ZM2,5H7L4.5,
                     7.5Zm6,9H22v2H8ZM2,14H7L4.5,16.5Zm6,
                     4H22v1.5H8Z"
                fill="currentColor"
            />
        </svg>
    );
}
```
---

| Pros                                                    | Cons                         |
| ------------------------------------------------------- | ---------------------------- |
| Can offer options with props (since it's in a function) | More HTML, BUT JS will cache |
| Can target individual parts of the SVG with CSS         |                              |
| Scales easily                                           |                              |
| Easy to update/maintain                                 |                              |

* This is what we use in the KB

---
## Further Reading

https://css-tricks.com/using-svg/

https://css-tricks.com/svg-symbol-good-choice-icons/

https://www.oreilly.com/library/view/building-web-applications/9780735675742/

---

## Questions

![](https://media.giphy.com/media/xUOxfjsW9fWPqEWouI/giphy.gif)