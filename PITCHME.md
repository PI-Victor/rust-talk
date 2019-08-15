@title[Rust]


@img[rust-logo.png](./assets/img/serveimage.png)
#### Rust

A multi-paradigm system programming language

@snap[bottom text-05]
@quote[Rust was the 'most loved programming language' in the Stack Overflow Developer Survey for 2016, 2017, 2018, and 2019.- Wikipedia]
@snapend

---
@snap[text-center text-06]
Main features
<hr width=20%>
@ul
- does not have garbage collector
- default memory allocation is done on the stack (programatically on the heap)
- none (or very small) runtime 
- memory management is done through the ownership system (no null pointers, thus no dangling pointers or data races)
- by default defined variables are immutable
- idiomatic rust is (almost) as fast as idiomatic c/c++
- edition system (two year release cycle ironically - 2015, 2018)
@ulend
@snapend
---
@snap[text-center text-06]
The tool chain  
<hr width=20%>
@ul
- rustc is the cross-compiler, linker "manipulator" and linter
- rustfmt will format code according to spec
- rustdoc generates code documentation out of code files or markdown (cargo doc)
- rust-lldb rust-gdb are used for debugging 
- rustup an installer for the rust toolchain 
- clippy is an advanced rust linter 
- sscache for caching deps and cutting down compile time (experimental support)
@ulend
@snapend
---

@snap[text-center text-06]
Caveats
<hr width=20%>
@ul
- can only statically compile with musl https://doc.rust-lang.org/1.5.0/book/advanced-linking.html
- default compilation can seem slow (non-optimized)
- optimized compilation (release) is even slower
- RLS (rust language server) can be a PITA at times
- most libraries are very new and some, sadly, stale
@ulend
@snapend
---
@snap[north]
Cargo
<hr width=20%>

@size[22px](Highly customizable package manager)
@snapend

@snap[west text-left text-04]
@ul
- cargo init/new (--bin default) for binaries --lib for libraries
- cargo test runs unit and integration 
- cargo bench runs the rust integrated benchmarks against your repo
- cargo package/publish will package and push a package to the crates.io registry
@ulend
@snapend
@snap[east text-left text-04]
Cargo.toml
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
@snapend
---
Ownership

---
This is the borrow checker
![yoda](./assets/yoda.jpeg)

---
This is you handling the borrow checker
![balance](./assets/balance.png)

---
@snap[midpoint text-06]
[Ownership](https://repl.it/@PI_Victor/ownership)
@ul
- a variable becomes a value's owner
- two variables can not own the same value
- when the owner is out of scope, the value is dropped
- a borrow can have either one or more refs (&T) or one mutable ref (&mut T) but not both
@ulend
@snapend
---

@snap[midpoint text-06]
[Lifetimes](https://repl.it/@PI_Victor/lifetimes)
@ul
- a variable's lifetime begins when it is created and ends when it is destroyed
- ellision was introduced to strip away a lot of lifetime boilerplate annotations (available for functions, since they don't have to correlate with anything else)
- you cannot annotate variables with lifetimes
- a lifetime is specified by the caller and cannot be changed or assigned by the callee
- a borrowed pointer can only refer to a value that has a longer lifetime than its own lifetime
- the rust compiler only checks function signatures, not functions body 
@ulend
@snapend
---
@snap[midpoint text-06]
@size[11px]([Structs](https://repl.it/@PI_Victor/structs))
@ul
- fields/functions are by default private
- they accept generic type parameters
- there is no type initialization or inferrence for fields
- methods are attached to a function inside the impl block and take self as param
@ulend
@snapend
---
[Traits and Generics](https://repl.it/@PI_Victor/traits-and-generics)
@snap[midpoint text-06]
- for traits static methods can be defined or instance methods (self)
- traits can provide default method definitions
- types can be bound to traits when passed as generic types
- generics are accepted by: functions, structs, enums and traits

@snapend
---
[Error handling](https://repl.it/@PI_Victor/error-handling)
@snap[midpoint text-06]
@ul
- return values are handled by the Option<T> enum
- unwrap panics if the result is Err or None othwerwise it unwraps Ok(T) from Result, should be used when you don't expect an error
- ? will return the Result type up to the caller to be handled without panicking
- expect is similar to unwrap but you can set a custom error message
@ulend
@snap
---
[Pattern matching](https://repl.it/@PI_Victor/pattern-matching)

---