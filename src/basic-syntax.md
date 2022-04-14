# Comments

```rust
// This is a comment
/* This is a
    multiline comment */
```

# Basic types

| Type    | Description                                                                                                                                                                         |
|---------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `u32`   | Unsigned 32 bit integer. Also have `u8`, `u16`, `u64`, and `u128`. When an architecture is unable to support an integer width, it will be emulated in software.                     |
| `i32`   | Signed 32 bit integer. Also have `i8`, `i16`, `i64`, and `i128`.                                                                                                                    |
| `usize` | Unsigned integer that is atleast large enough to hold a memory address. Also have `isize` for signed. `usize` is commonly used as the size type of container classes such as `Vec`. |
| `f32`   | 32 bit floating point number. Also have `f64`.                                                                                                                                      |
| `bool`  | Boolean value.                                                                                                                                                                      |

# Functions

```rust
// Arguments a and b both have type u32
// Return type is also u32
fn add(a: u32, b: u32) -> u32 {
    return a + b;
}

// Functions could return nothing
// This is the C/C++ equivalent of a void return type
fn foo(a: bool) {
    // Code goes here
}

// There is a special return type called never for functions that never return
fn start_web_server() -> ! {
    // Loop forever
}
```

# Control flow

```rust
fn difference(a: u32, b: u32) -> u32 {
    // No need to put parentheses () around the conditional
    if a < b {
        return b - a;
    }
    else if b < a {
        return a - b;
    }
    else {
        return a - b;
    }
}
```

# Variables

```rust
fn add(a: u32, b: u32) -> u32 {
    // It is not possible to create a variable without assigning a value to it
    let result: u32 = a + b;

    // Types can omitted if the compiler is able to figure it out based on context
    let product = a * b;

    return result;
}
```

Rust is a statically types language so all variables must have a type that can be determined at compile time.
However, the compiler is quite clever which often lets us omit types.
