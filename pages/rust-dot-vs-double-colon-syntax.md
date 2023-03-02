Crates and types are namespaces. Double colons are for namespaces like dots are for values.

The following is from [A half-hour to learn Rust](https://fasterthanli.me/articles/a-half-hour-to-learn-rust) 

Dots are typically used to access fields of a value:

```rust
let a = (10, 20);
a.0; // this is 10

let amos = get_some_struct();
amos.nickname; // this is "fasterthanlime"
```

Or call a method on a value:

```rust
let nick = "fasterthanlime";
nick.len(); // this is 14
```

The double-colon, `::`, is similar but it operates on namespaces.

In this example, `std` is a _crate_ (~ a library), `cmp` is a _module_ (~ a source file), and `min` is a _function_:

```rust
let least = std::cmp::min(3, 8); // this is 3
```

`use` directives can be used to "bring in scope" names from other namespace:

```rust
use std::cmp::min;

let least = min(7, 1); // this is 1
```

Within `use` directives, curly brackets have another meaning: they're "globs". If we want to import both `min` and `max`, we can do any of these:

```rust
// this works:
use std::cmp::min;
use std::cmp::max;

// this also works:
use std::cmp::{min, max};

// this also works!
use std::{cmp::min, cmp::max};
```

A wildcard (`*`) lets you import every symbol from a namespace:

```rust
// this brings `min` and `max` in scope, and many other things
use std::cmp::*;
```

Types are namespaces too, and methods can be called as regular functions:

```rust
let x = "amos".len(); // this is 4
let x = str::len("amos"); // this is also 4
```

`str` is a primitive type, but many non-primitive types are also in scope by default.

```rust
// `Vec` is a regular struct, not a primitive type
let v = Vec::new();

// this is exactly the same code, but with the *full* path to `Vec`
let v = std::vec::Vec::new();
```

This works because Rust inserts this at the beginning of every module:

```rust
use std::prelude::v1::*;
```

(Which in turns re-exports a lot of symbols, like `Vec`, `String`, `Option` and `Result`).

