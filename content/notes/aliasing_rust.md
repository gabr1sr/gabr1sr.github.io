+++
title = "Aliasing (Rust)"
author = ["Gabriel Rosa"]
date = 2024-01-13T16:13:00-03:00
tags = ["rust", "type", "aliasing"]
draft = false
+++

tags
: [Tipagem (Rust)]({{< relref "tipagem_rust.md" >}})

source
: [Aliasing - Rust By Example](https://doc.rust-lang.org/stable/rust-by-example/types/alias.html)

A palavra-chave `type` pode ser utilizada para dar um novo nome a um tipo existente.

O nome dos tipos devem seguir o padrão `UpperCamelCase` ou o compilador irá soltar um alerta.

A exceção dessa regra são os tipos primitivos: `usize`, `f32`, etc.

```rust
type NanoSecond = u64;
type Inch = u64;
type U64 = u64;

fn main() {
    // NanoSecond = Inch = U64 = u64
    let nanoseconds: NanoSecond = 5 as U64;
    let inches: Inch = 2 as U64;

    println!("{} nanoseconds + {} inches = {} unit?", nanoseconds, inches, nanoseconds + inches);
}
```
