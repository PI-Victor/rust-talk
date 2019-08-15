@title[Rust]


![rust-logo.png](./assets/img/serveimage.png)
#### Rust

A multi-paradigm system programming language

@snap[position bottom]
@quote[Rust was the 'most loved programming language' in the Stack Overflow Developer Survey for 2016, 2017, 2018, and 2019.](Wikipedia)
@snapend

---
Main features

@ul
- does not have garbage collector
- default memory allocation is done on the stack (programatically on the heap)
- none (or very small) runtime 
- memory management is done through the ownership system (no null pointers, thus no dangling pointers or data races)
- default value imutability
- idiomatic rust is (almost) as fast as idiomatic c/c++
- Edition system (two year release cycle)
@ulend

---
The tool chain  

@ul
- rustc is the cross-compiler, linker "manipulator" and linter
- rustfmt will format code according to spec
- rustdoc generates code documentation out of code files or markdown (cargo doc)
- rust-lldb rust-gdb are used for debugging 
- rustup an installer for the rust toolchain 
- clippy is an advanced rust linter 
- sscache for caching deps and cutting down compile time (experimental support)
@ulend

---
Caveats
@ul
- can only statically compile with musl https://doc.rust-lang.org/1.5.0/book/advanced-linking.html
- default compilation can seem slow (non-optimized)
- optimized compilation (release) is even slower
- RLS (rust language server) can be a PITA at times
- most libraries are very new
@ulend

---
Cargo

@size[20px](Highly customizable package manager.)

@ul
- cargo init/new (--bin default) for binaries
- cargo test runs unit and integration 
- cargo bench runs the rust integrated benchmarks against your repo
- cargo package/publish will package and push a package to the crates.io registry
@ulend

---

```toml
[package]
name = "test"
version = "0.1.0"
edition = "2018"
build = "build.rs"
links = "foo"

exclude = ["build/**/*.o", "doc/**/*.html"]
include = include = ["**/*.rs","Cargo.toml"]
publish = ["my-registry"]

[dependencies]
clap = "~2.33.0"
config = "0.9"
serde = "~1.0"
```

---
Ownership

---
Borrow checker
![yoda](./assets/yoda.jpeg)

---
Handling the borrow checker
![balance](./assets/balance.png)

---
[Ownership](https://repl.it/@PI_Victor/ownership)
- A variable becomes a value's owner
- Two variables can not own the same value
- When the owner is out of scope, the value is dropped

---
Lifetimes

@ul
- A lifetime begins at its creation and ends when it is destroyed
- [Elission was introduced to strip away a lot of lifetime boilerplate annotations](https://repl.it/@PI_Victor/elision)
- 'static - a special lifetime that persists until the end of the program (can be coerced)
@ulend
---
Traits

