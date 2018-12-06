# __SVG__ is your friend!



![](https://media.giphy.com/media/CHmwA02GQ6aTS/giphy.gif)

---

## What's an __SVG__?

SVG is an image format. Here's an example: the FireFox logo.


![right](https://upload.wikimedia.org/wikipedia/commons/6/67/Firefox_Logo%2C_2017.svg)

---
##What does __SVG__ stand for?

- Scalable
- Vector
- Graphics

[>> Wikipedia Article](https://en.wikipedia.org/wiki/Scalable_Vector_Graphics)

---
## That's nice... what does it mean?

- Scales to any size (scalable)
- Described with "math" (vector)
- No loss of resolution (great for retina screens)
- Light weight (20 KB for SVG, 100x100px jpeg is 53 KB)
- Great for icons

---

## Openning an SVG file

![left](https://upload.wikimedia.org/wikipedia/commons/6/67/Firefox_Logo%2C_2017.svg)

- Browser
- Vector Graphics Program (such as Illustrator or Sketch)
- Text Editor

[>> Download](https://upload.wikimedia.org/wikipedia/commons/6/67/Firefox_Logo%2C_2017.svg)

---

# AHHHHHH!!!!!!!

![](https://media.giphy.com/media/5qoRdabXeT4GY/giphy.gif)

---

## Ok calm, down, I know that file looked scary, but let's look at simple square...

![left](./media/box.svg)

---

```XML
<?xml version="1.0" encoding="utf-8"?>
<!-- Generator: Adobe Illustrator 23.0.1, SVG Export Plug-In . SVG Version: 6.00 Build 0)  -->
<svg version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
	 viewBox="0 0 100 100"  width="100" height="100" style="enable-background:new 0 0 100 100;" xml:space="preserve">
	<style type="text/css">
		.st0{fill:#0031FF;stroke:#FF0000;stroke-miterlimit:10;}
	</style>
	<rect x="15.5" y="14.7" class="st0" width="69.1" height="69.1"/>
</svg>

```
---

# Better...

![](https://media.giphy.com/media/8OJdqYqN1Nii3UTD6l/giphy.gif)

---


Let's take our the noise and break it down.

```XML
<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" viewBox="0 0 100 100">
	<rect fill="#0031FF" stroke="#FF0000" x="15" y="15" width="70" height="70"/>
</svg>
```

---

## Pieces

- xmlns: format
- width, height
- viewBox (more to come)
- rectangle element, with position and size

---

## What's with the weird CSS?

It's not CSS. SVG predates a lot of the modern CSS styles we are used to. You can express styles __either__ with the SVG format, or the more modern CSS through `styles` or through regular css classes/id.

---

## View Box

- x position
- y position
- width
- height

See HTML example

---
# Further reading

Implementation in the next Lunch & Learn!

https://www.sarasoueidan.com/blog/svg-coordinate-systems/

https://www.oreilly.com/library/view/building-web-applications/9780735675742/

---
# Questions


![](https://media.giphy.com/media/xUOxfjsW9fWPqEWouI/giphy.gif)