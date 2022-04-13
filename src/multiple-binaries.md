# Multiple binaries

By default, cargo expects to find a `main.rs` file with an entry point that it can use to create a binary.
Instead, we could create a project with multiple binaries:

## Structure

```
Cargo.toml
src/
    client.rs
    server.rs

examples/
    hello_world_example.rs

target/        <- Compiled binaries found here
    debug/
        client
        server
        examples/
            hello_world_example
```

## Cargo.toml

```toml
[package]
name = "multiple-binaries"
version = "0.1.0"
edition = "2021"

[[bin]]
name = "client"
path = "src/client.rs"

[[bin]]
name = "server"
path = "src/server.rs"
```

## src/client.rs

```rust
fn main() {
    println!("I am a client.");
}
```

## src/server.rs

```rust
fn main() {
    println!("I am a server.");
}
```

## examples/hello_world_example.rs

```rust
fn main() {
    println!("I am an example.");
}
```

Use `cargo run` with the `--bin` or `--example` arguments to specify which binary to run:

```shell
cargo run --bin client
cargo run --bin server
cargo run --example hello_world_example
```

The `examples/` directory is a special location where we can place code samples for users to run with demo data.
For example, if we were creating a graphics renderer we could include some demo scenes as examples.
