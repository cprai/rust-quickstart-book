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
| `char`  | 32 bit Unicode Scalar Value used to hold a single character. This is enough bits to store any Unicode character in a single `char`.                                                 |

These types come with many useful constant values such as: `f32::NAN`, `std::f32::consts::PI`, `u32::MAX`, etc.

Notice that there is no empty type such as `null`, `nil`, `undefined`, or `None` like we might see in other languages.
In rust, similar behaviour can be achieved using the `Option<>` type which we will see later.

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

# Variables and literals

```rust
fn variables(a: u32, b: u32) {
    // It is not possible to create a variable without assigning a value to it
    let sum: u32 = a + b;

    // Types can omitted if the compiler is able to figure it out based on context
    let product = a * b;

    return sum;
}

fn literals() -> f32 {
    // char literals should be surrounded by single quotes ''
    let heart_eyed_cat: char = '😻';
    let pile_of_poo: char = '\u{1F4A9}';

    let boolean_value: bool = true;
    let other_boolean_value: bool = false;

    // Literals have built in type annotation
    let integer_value: u16 = 15u16;
    let other_integer_value: i64 = -54i64;
    let float_value: f64 = 23.532f64;

    // This is another case where types can be omitted
    let omit_variable_type = 43u32;
    let omit_literal_type: u32 = 43;

    // Literals can contain underscores _ for readability
    let one_million = 1_000_000_u32;

    let usize_value = 27_usize;
    let isize_value = -14_isize;
    let float_32_pi = 3.14159_f32;
    let float_32_accurate_pi = std::f32::consts::PI;
    let float_64_nan = f64::NAN;
    let u32_max_value = u32::MAX;

    // Ways to specify integers
    let decimal = 23_u32;
    let hex = 0x_fa_42_u16;
    let octal = 0o_72_u8;
    let binary = 0b_1111_0000_u8;

    let dense_hex: u16 = 0xfa42;
    let dense_octal: u8 = 0o72;
    let dense_binary: u8 = 0b11110000;

    // The float type here can be inferred through the function return type
    return 2.71828;
}
```

Rust is a statically typed language so all variables must have a type that can be determined at compile time.
However, the compiler is quite clever which often lets us omit types.
There are some ambitious scenarios where the compiler may choose a default without raising a warning.
Best practice is to always be as explicit as possible.

### Quiz:

Does the following statement result in a sign extension?

```rust
let octal = 0o_72_i8;
```
