# Unit testing

The easiest way to do unit testing is to create functions marked with the `#[test]` macro.
We can do this anywhere within the crate.

We haven't talked about function syntax yet but for now we will use the following add function:

```rust
fn add(a: u32, b: u32) -> u32 {
    a + b
}
```

A unit test looks like this:

```rust
#[test]
fn test_add() {
    assert_eq!(add(7, 12), 19);
    assert_ne!(add(8, 8), 0);
}
```

`#[test]`, `assert_eq!()`, and `assert_ne!()` are all macros.

## src/main.rs

```rust
fn main() {
    println!("Hello, world!");
}

fn add(a: u32, b: u32) -> u32 {
    a + b
}

#[test]
fn test_add_0() {
    assert_eq!(add(7, 12), 19);
}

#[test]
fn test_add_1() {
    assert_eq!(add(23, 56), 79);
}

#[test]
fn test_add_2() {
    assert_ne!(add(2, 2), 5);
}
```

Use `cargo test` to run all unit tests:

```
$ cargo test
   Compiling unit-testing v0.1.0 (/tmp/unit-testing)
    Finished test [unoptimized + debuginfo] target(s) in 0.31s
     Running unittests (target/debug/deps/unit_testing-e0254e70a2565982)

running 3 tests
test test_add_0 ... ok
test test_add_1 ... ok
test test_add_2 ... ok

test result: ok. 3 passed; 0 failed; 0 ignored; 0 measured; 0 filtered out; finished in 0.00s
```

There is no guarantee on the order in which tests will be run.

# Running a subset of tests

We can run only a specific test by its name:

```shell
cargo test test_add_1
```

We can also specify a range of tests:

```shell
cargo test test_add_
```

This will run all tests which contain the substring `test_add_`.

# Tests module

Rust convention is to have unit tests in the same file as the code that is being tested but in a submodule.
Having it in the same file makes it more convenient to update the tests when updating the code.
Having it in a submodule avoids namespace pollution from all the test functions being created.

## src/main.rs

```rust
fn main() {
    println!("Hello, world!");
}

fn add(a: u32, b: u32) -> u32 {
    a + b
}

#[cfg(test)]
mod tests {
    use super::add;

    #[test]
    fn test_add_0() {
        assert_eq!(add(7, 12), 19);
    }

    #[test]
    fn test_add_1() {
        assert_eq!(add(23, 56), 79);
    }

    #[test]
    fn test_add_2() {
        assert_ne!(add(2, 2), 5);
    }
}
```

* `mod tests { ... }` creates a submodule called tests.
* `use super::add;` imports the `add()` function from the containing module.
* `#[cfg(test)]` tells cargo to only compile this code when running `cargo test` and not in a normal build.
