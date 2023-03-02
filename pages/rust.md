[[rust-dot-vs-double-colon-syntax]]

[Rust for the impatient - YouTube](https://www.youtube.com/watch?v=br3GIIQeefY&t=320s)
[A JavaScript developer learning Rust #1 - YouTube](https://www.youtube.com/watch?v=55uFgogVms8)

## Mutable reference (&mut)

```rust
fn (&mut foo) {

}
```

Pass the function a mutable reference to foo.

> The `&` indicates that this argument is a _reference_, which gives you a way to let multiple parts of your code access one piece of data without needing to copy that data into memory multiple times. References are a complex feature, and one of Rust’s major advantages is how safe and easy it is to use references. You don’t need to know a lot of those details to finish this program. For now, all you need to know is that like variables, references are immutable by default. Hence, you need to write `&mut guess` rather than `&guess` to make it mutable.
> – From [The Rust Book](https://doc.rust-lang.org/stable/book/ch02-00-guessing-game-tutorial.html#receiving-user-input)

