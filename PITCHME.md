@title[Rust]


![rust-logo.png](assets/img/serveimage.png)
#### Rust

A multi-paradigm system programming language

@snap[position bottom]
@size[small]()
@quote[Rust was the "most loved programming language" in the Stack Overflow Developer Survey for 2016, 2017, 2018, and 2019.](Wikipedia)
@snapend

---
Main features

@ul
- does not have garbage collector
- default memory allocation is done on the stack
- static code analysis at compile time
- small runtime (c/c++)
- does not have null pointers, dangling pointers or data races
- ownership 
- default variable imutability

@ulend

---
The tool chain  

@ul
- rustc is the cross-compiler, linker "manipulator" and linter
- rustfmt will format code according to spec
- rustdoc generates code documentation out of code files or markdown
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
@ulend

---
@size[22px](Cargo)
