# Creating a project

Use `cargo new` to start a new project:

```shell
cargo new demo-project
```

This will create a new directory named `demo-project` with the following files:

```
.git/<git-stuff>  <- Cargo automatically initializes a git repository for us
.gitignore
Cargo.toml        <- Cargo.toml contains project metadata used by the build system
src/
    main.rs       <- Project source code
```

The filename `main.rs` is important because we are creating a bin project.
Alternatively, we could create a lib project:

```shell
cargo new --lib demo-project
```

This generates:

```
.git/<git-stuff>
.gitignore
Cargo.toml
src/
    lib.rs
```

Bin projects are the default for `cargo new` but the following command is also valid:

```shell
cargo new --bin demo-project
```

Bin projects produce executable binaries while lib projects produce libraries to be used by other projects.
We will ignore lib projects for now.

# Boilerplate files

Let's have a closer look at these generated files.

## Cargo.toml

```toml
[package]
name = "demo-project"
version = "0.1.0"
edition = "2021"

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html

[dependencies]
```

`package.name` and `package.version` are both required keys. `package.edition` tells cargo which rust edition to use.
The rust [edition](https://doc.rust-lang.org/stable/edition-guide/) is not the same thing as the rust version.
For example, code that is written for edition 2021 could interoperate seamlessly with code that is written for edition
2018 as long as we use a rust version that supports at least edition 2021.

Under dependencies, we can specify external libraries that we would like to use.
These external libraries are called crates.
The cargo registry can be used to look up available crates at [https://crates.io/](https://crates.io/).
Our own project would also be referred to as a crate.

## src/main.rs

```rust
fn main() {
    println!("Hello, world!");
}
```

Like with a C/C++ project, rust expects a `main()` function which will used as the entry point of the program.
It is possible to compile without a main function or without the rust standard library for bare metal programming.

`println!()` is a macro which will print to stdout. We will talk more about macros later.

# Build and run

Use `cargo build` to compile:

```shell
cargo build
cargo build --debug          # <- Default behaviour
cargo build --release
```

This will produce a `target/` directory with the following binaries:

```
./target/debug/demo-project
./target/release/demo-project
```

Use `cargo run` to both compile and then run:

```shell
cargo run
cargo run --debug            # <- Default behaviour
cargo run --release
```

Use `cargo clean` to delete the `target/` directory.
