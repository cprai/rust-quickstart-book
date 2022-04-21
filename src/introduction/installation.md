# Installation

The officially supported way to install rust is through [rustup](https://www.rust-lang.org/tools/install).
This should also install all necessary build dependencies.
On Windows, Visual Studio C++ Build Tools may also be required.

Once installed, we should have the following command line utilities:
* `rustup` is a utility to manage rust compiler installations.
* `rustc` is the rust compiler and linker. The rust compiler is based on llvm.
* `rustdoc` is a documentation generation tool.
* `rustfmt` is an opinionated code formatting tool to settle formatting arguments.
* `cargo` is a build tool to manage projects and dependencies.

We should also get the following debuggers:
* `rust-gdb`
* `rust-lldb`

We should not need to interface with `rustc` directly if we are using `cargo` to build and run our projects.

These tools are extensively documented:
* [rustup book](https://rust-lang.github.io/rustup/)
* [rustc book](https://doc.rust-lang.org/stable/rustc/)
* [rustdoc book](https://doc.rust-lang.org/stable/rustdoc/)
* [rustfmt docs](https://rust-lang.github.io/rustfmt/)
* [cargo book](https://doc.rust-lang.org/stable/cargo/)
