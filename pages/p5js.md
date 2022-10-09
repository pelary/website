---
title: p5js
---

p5js.


## Patterns

A vector with random x,y

```js
createVector(random(width), random(height));
```



## A physics engine in P5js

A physics engine built on accelleration, following Nature of Code 2.0 video series:

- [I.0: Introduction - The Nature of Code - YouTube](https://www.youtube.com/watch?v=6vX8wT1G798&list=PLRqwX-V7Uu6YVljJvFRCyRM6mmF5wMPeE) (previous edition)
- [The Nature of Code 2 - YouTube](https://www.youtube.com/playlist?list=PLRqwX-V7Uu6ZV4yEcW3uDwOgGXKUUsPOM)

`Force = Mass * Accelleration`. Acceleration is just another [[vector]]. When we apply acceleration it doesn't necessarily mean we're speeding up, it could be any change expressed in motion.

### "Motion 101"

```
	update() {
		this.vel.add(this.acc);
		this.pos.add(this.vel);
	}
```

Add random acceleration (and slow it down to see what's going on)

```js
this.acc = p5.Vector.random2D();
this.acc.setMag(0.01);
```

`limit()` caps the magnitude.

## Convex hull / path finding / gift wrapping algorithm

[Coding Challenge #148: Gift Wrapping Algorithm (Convex Hull) - YouTube](https://www.youtube.com/watch?v=YNyULRrydVI&feature=youtu.be)

A convex shape does not have angles larger than 180 degress. A concave shape can have an angle larger than 180 degrees, for example a pac-man face shape, a pizza with a slice taken out, is a concave shape, because the internal angle at the center (where the piece is missing) is larger than 180 degrees.

A "convex hull" is a shape that does not have angles larger than 180 degrees and that contains all points.

We start with a known point on the hull – for example, the left-most point. We then check all remaining points against it, and choose the left-most point again (for every point on the hull, left would point away from the shape and right would point toward the center of the shape). Eventually, the left-most point will be the point we started out with. 
