---
title: 2D Platformer in Godot
---

Classic 2D platformer, pretty much. Platforms, hazards, enemies, limited lives, items. Simple game UX, with a level scene, a game over screen, and a victory screen.

## Project setup and Godot

Graphics, including a layered background, player, enemy, and particle sprites, environment tiles, sound effects, music, and a dynamic font.

### Canvas and Animation

Animation runs in a continuous loop with a predefined framerate.

A canvas is drawn from top-left, so, for example:

- Right is `x+`
- Left is `x-`
- Up is `y-`
- Down is `y+`

That's my own _intuitive_ notation. Godot actually represents this as a vector, so for example, up is `Vector2(0,-1)`.

Delta is the time in seconds between frames.

### 2D Physics in Godot

- `PhysicsBody`
  - `StaticBody` - for things that don't move.
  - `RigidBody` - for things that react to the environment.
  - `KinematicBody` - for things that are controlled directly (either by the player or the engine/ai?)

These are containers for other nodes that hold the actual content, like sprites, collision shapes, etc.

(The way to actually make all these nodes behave as a group in the editor is to check "Makes sure the object's children are not selectable".)

- `move_and_collide()` - stop on collision.
- `move_and_slide()` - slide along collided body. Uses `delta` from `_physics_process()`.

`move_and_slide()` takes a `Vector2` which is the velocity, in pixels per second. The second argument is `up_direction` which is also a `Vector2`. The default is `(0,0)`. For our platformer, moving up means adding a negative number to `y`. So the second argument should be `Vector2(0,-1)`. For example:

```gdscript
const UP = Vector2(0,-1)
# movement code...
move_and_slide(velocity,UP)
```

By specifying the direction for up, we can use functions like `is_on_floor()`.

### Input

Godot projects start with a few input actions already defined, such as `ui_left` and `ui_right`, but apparently these are meant to be used with the game's UI, such as menus. I guess it raises the accessibility baseline.

Actions are added and edited in Project > Project Settings > Input Map. No obvious way to import/export from this screen, so here are the settings I used:

- Left
  - A
  - Left
  - Device 0, Button 14 (D-Pad Left).
  - Device 0, Axis 0 - (Left Stick Left).
- Right
  - D
  - Right
  - Device 0, Button 15 (D-Pad Right).
  - Device 0, Axis 0 + (Left Stick Right).
- Jump
  - W
  - Space
  - Up
  - Device 0, Button 0 (DualShock Cross, Xbox A, Nintendo B).
  - Device 0, Button 1 (DualShock Circle, Xbox B, Nintendo A).
  - Device 0, Axis 1 - (Left Stick Up).

To check for them in code, we have the built-in Input class ("A singleton that deals with inputs"). For example:

```gdscript
if Input.is_action_pressed("left"):
```

## Loop (`_physics_process()`)

We check all inputs to see if there is any velocity, end up with some total velocity to make, and call `move_and_slide()` with that velocity to make it happen.

In practice we store velocity as a global variable of type `Vector2`.

Initially it is `(0,0)` because we start out standing still.

We also define a speed and a gravity.

We now start a loop, and a bunch of different functions get loaded at different points for each iteration through it. `_physics_process()` is where we'll do most of our work.

So every frame, based on inputs, we can derive horizontal velocity from speed and vertical velocity from gravity (by doing `velocity.x = SPEED` to go right or `velocity.y += GRAVITY` to fall down, for example.)

### Gravity

Add a gravity constant to vertical velocity whenever not on floor (`velocity.y += GRAVITY`).

When on floor, set zero vertical velocity (`velocity.y = 0`.)

### Jumping

To jump, we add a large negative value to `velocity.y` – our jump speed. However, our jump should have limits. For example, we can use `is_on_floor()` to check if the player is able to jump. We can use `is_on_floor()` if we defined the up direction.

This will cause the player to go up until the jump speed elapses. If it hits an obstacle, it will not behave correctly – it will effectively floats while there's still jump speed left.

We can use `is_on_ceiling()` to detect when the player has hit an obstacle, and then reset `velocity.y`. Setting `velocity.y` to `1` will result in moving one pixel down in the next frame, after which the player will continue to fall normally (since they moved one pixel down, they're no longer on the ceiling).

### Moving

Add speed to velocity.x based on direction

Also flip the sprite?

### Falling

We can set a constant to limit the play area and define a boundary beyond which the player "falls" and dies. For example:

```gdscript
const ABYSS = 1000
# ...
if position.y > ABYSS:
	game_over()
```

### Graphics

The actual textures for the player are stored in an AnimatedSprite as separate animations. We can call them from our script.

We check `velocity.y` to see if we're jumping and `velocity.x` to see if we're walking, and if neither is true we're "idle". Which we can create an animation for.

## Changing scenes

We can change scenes to change levels, we can restart the scene to restart the level (if the player dies for e.g.), and we can switch scenes for a victory screen, a game over screen, etc.

## Player

- KinematicBody2D (script)
  - Sprite (texture)
  - CollisionShape2D (shape)

This is the basic outline for a Player "scene" (a node class, basically). The script is a resource of the main node. The texture is a resource of the Sprite node. The collision shape is a resource of the CollisionShape node.

There is also an AnimatedSprite node which seems to be less of a hassle to use.

## Levels?

- Node2D
  - \*Player
  - StaticBody2D
    - Sprite
    - CollisionShape2D

This is a basic "level", which has a player and a platform (the StaticBody).

## AnimatedSprite

A sprite that animates itself, unlike a regular Sprite which can be animated with an AnimationPlayer node.

Can have multiple animations, so AnimationPlayer may still be involved in switching them, for example.

Simpler to use I guess? There's a way to create an AnimatedSprite node from a spritesheet directly.

## Camera

The camera can be a part of the Player's tree. It has a few useful properties we can modify, like zoom, smoothing, and limits.

For our game we want to use a transform to move the camera to the left (so the screen shows more of what's "ahead" and less of what's "behind"), set limits so the camera can't reach beyond the edges of the level, and mess around with smoothing to see what works best.

For example, if the top left corner of the level is at (0,0), the top and left limits should be set to 0 accordingly. When the player moves left towards the edge of the level, the camera will stop following once it reaches (0,0). If the player keeps going, they'll move away from the center of the screen but the camera will stay put.

## Tiles

A `Tilemap` node can have a `TileSet` resource. It has its own editor in the bottom panel. Inside the resource are textures and inside each texture are tiles. Godot 3.2 has some automation for drawing maps with tiles, specifically Auto Tiling, which helps pick correct tiles around borders/outlines of areas. Mostly though it seems to be a very manual and annoying process to set up a TileSet resource in Godot.

(Here's some pretty random discussion about it: [New TileSet editor and TileMap improvements · Issue #896 · godotengine/godot-proposals](https://github.com/godotengine/godot-proposals/issues/896#issuecomment-667157872). Doesn't look like it's getting worked on, at least on this thread.)

## Parallax Background

[CanvasLayer](https://docs.godotengine.org/en/stable/classes/class_canvaslayer.html#class-canvaslayer) is like a separate layer with its own transform, that can move separately from the rest of the game (or not move at all.) We can use it for UI, and Godot also has a dedicated ParallaxBackground node for creating parallax backgrounds in ParallaxLayer nodes which have TextureRect nodes.

Tiling is defined as "Mirroring" on the ParallaxLayer.

## Game Over Scene

- Control (Layout Full Rect)
  - TextureRect (with Expand enabled and layout set to Full Rect)
  - CenterContainer
    - VBoxContainer
      - (etc.)

[Control](https://docs.godotengine.org/en/stable/classes/class_control.html#control) nodes are useful for creating UIs. Layouts can be built with row/columns layouts and grids. Doesn't feel very different from CSS.

Buttons can be made interactive by connecting their signals, for e.g. `pressed()`:

```gdscript
func _on_Button_pressed():
	get_tree().change_scene()
```
