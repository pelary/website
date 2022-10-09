---
title: css
---

## Flexbox

```css
display: flex;
```

Layout children along a single axis. Horizontal or vertical, a column or a row. Horizontal by default. Wrapping is optional.

```css
flex-direction: row; /* side-to-side, same as text direction */
flex-direction: row-reverse; /* side-to-side, opposite direction */
flex-direction: column; /* top-to-bottom */
flex-direction: column-reverse; /* bottom-to-top */
```

This direction is the "main axis" according to the spec. The secondary or perpendicular axis is called the "cross axis".

```css
justify-content: flex-start;
```

Align children along the main axis.

```css
align-items: stretch | flex-start | flex-end | center | baseline | first
	baseline | last baseline | start | end | self-start | self-end;
```

Align children along the cross axis.

```css
align-content: flex-start | flex-end | center | space-between | space-around |
	space-evenly | stretch | start | end | baseline | first baseline | last
	baseline;
```

When flex items wrap, this determines the distribution along the cross axis. For example, for `flex-direction: row`, the main axis is side-to-side. If it wraps, then `align-content` will affect the space between the rows top-to-bottom.

More flexbox:

- [Learn Flexbox in 15 Minutes - YouTube](https://www.youtube.com/watch?v=fYq5PXgSsbE)
- [A Complete Guide to Flexbox | CSS-Tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

## CSS Grid

`fr` is a relative unit that represents some fraction of the available space in the container.

- [Basic Concepts of grid layout - CSS: Cascading Style Sheets - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout/Basic_Concepts_of_Grid_Layout)

## Unicode

| code         | symbol      |
| ------------ | ----------- |
| `'\2013\20'` | endash: `–` |

## Media queries

- [Media Queries for Standard Devices - CSS-Tricks](https://css-tricks.com/snippets/css/media-queries-for-standard-devices/)
- [Using media queries - CSS: Cascading Style Sheets - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)

```css
/* Portrait and Landscape */
@media only screen 
  and (min-device-width: 375px) 
  and (max-device-width: 667px) 
  and (-webkit-min-device-pixel-ratio: 2) { 

}

/* Portrait */
@media only screen 
  and (min-device-width: 375px) 
  and (max-device-width: 667px) 
  and (-webkit-min-device-pixel-ratio: 2)
  and (orientation: portrait) { 

}

/* Landscape */
@media only screen 
  and (min-device-width: 375px) 
  and (max-device-width: 667px) 
  and (-webkit-min-device-pixel-ratio: 2)
  and (orientation: landscape) { 

}
```

### Breakpoints

- 320px — 480px: Mobile devices
- 481px — 768px: iPads, Tablets
- 769px — 1024px: Small screens, laptops
- 1025px — 1200px: Desktops, large screens
- 1201px and more —  Extra large screens, TV

## Organization

For example:

```css
/* || General styles */
/* || Typography */
/* || Utilities */
/* || Site Wide */
/* || Header and Main Navigation */
/* || Other special cases */
```

- [Recipe: Media objects - CSS: Cascading Style Sheets | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Layout_cookbook/Media_objects)s
- [Organizing your CSS - Learn web development - MDN](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Organizing)
