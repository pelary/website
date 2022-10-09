---
title: Bootstrap
---

Bootstrap.


## Bootstrap Patterns

### Full Height / Full Screen / Dashboard

```html
		<div class="main container align-items-center h-100 container-fluid">
			<div class="row flex-fill">
```

- `.container-fluid` full width container, spanning the entire width of the viewport. [#](https://getbootstrap.com/docs/4.5/layout/overview/#fluid)
- `.d-flex` will set `display: flex`. [#](https://getbootstrap.com/docs/4.5/utilities/flex/#enable-flex-behaviors)
	- `display: flex` The element behaves like a block element and lays out its content according to the flexbox model.
	- `display: ineline-flex` The element behaves like an inline element and lays out its content according to the flexbox model.
	- [display - CSS: Cascading Style Sheets | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/display)
- `.flex-fill` Use the .flex-fill class on a series of sibling elements to force them into widths equal to their content (or equal widths if their content does not surpass their border-boxes) while taking up all available horizontal space. [#](https://getbootstrap.com/docs/4.5/utilities/flex/#fill)
	- Looks like it's setting `flex: 1 1 auto!important;`