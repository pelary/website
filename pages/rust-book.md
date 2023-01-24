Notes and commented code from [The Rust Programming Language](https://doc.rust-lang.org/stable/book/title-page.html) (The Rust Book)

## Guessing Game
```rust
use std::io;

fn main() {
    println!("Guess the number!");

    println!("Please input your guess.");

    // `let mut` variables are immutable by default
    // `=` means we want to bind something to the variable right now
    // the value that the variable gets bound to is the result of calling `String::new`
    // `String::new` is a function that returns a new instance of a String
    // String is provided by `std::` and is growable and UTF-8 encoded
    // `::new` indicates that `new` is an associated function of the String type
    let mut guess = String::new();

    io::stdin()
        .read_line(&mut guess)
        .expect("Failed to read line");

    println!("You guessed: {guess}");
}
```

