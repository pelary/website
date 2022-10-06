---
title: CSS
nav_order: 30
---

CSS

1. TOC
   {:toc}

## CSS Grid

`fr` is a relative unit that represents some fraction of the availabe space in the container. 

- [Basic Concepts of grid layout - CSS: Cascading Style Sheets - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout/Basic_Concepts_of_Grid_Layout)

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

`````` CSS
/* || General styles */
/* || Typography */
/* || Utilities */
/* || Site Wide */
/* || Header and Main Navigation */
/* || Other special cases */
```

- [Recipe: Media objects - CSS: Cascading Style Sheets | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Layout_cookbook/Media_objects)s
- [Organizing your CSS - Learn web development - MDN](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Organizing)
