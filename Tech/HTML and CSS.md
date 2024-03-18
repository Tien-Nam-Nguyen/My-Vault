---
type:
  - Tech
tags:
  - HTML
  - CSS
  - Frontend
published: true
folder: Tech
---

Html are composed of smaller elements, with each element has opening and closing tags:

>[!example]
>\<p\> This is some text\</p\>

Some tags just have one opening tag, called void elements:

>[!example]
>\<link rel="stylesheet" href="/.../..."\>

A basic html has following architecture:

```html
<!DOCTYPE html>     <!-- this tells browser to use the modern html version-->
<html>
	<head><\head>    <!-- contains element that are not visible-->
	<body><\body>    <!-- contains element that are visible-->
<\html>
```


Every element has two type of display:
- Block: take the full horizontal space of its box
- Inline-block: take the full box's space
- Inline: it is used for text

Here is some most used elements:
- \<img\>: it is a image placeholder
- \<input\>: a input like text box, check box, ...
- \<p\>: paragraph element
- \<div\>: container element, allows nesting
- \<strong\>: bold text
- \<style\>: contains css elements


# CSS

It is used to change the appearance of web pages.

```css
button {     /*it is applied for every button in html page*/
	height: 10px;
	width: 10px;
}

.specific_button {     /*it is applied for a specific class button*/
	height: 12px;
	width: 12px;
}

```

>[!note]
>It can be placed in a style element or placed in a css file

```css
<link rel="stylesheet" href="address of css file">	
```

You can create grid, flex in css to align instead of inline block:

```css
.some_style {
	display: grid;
	grid-template-columns: 10px 10px 1fr;
	row-gap: 20px;
	column-gap: 20px;
}
```
# References

https://www.youtube.com/watch?v=G3e-cpL7ofc
