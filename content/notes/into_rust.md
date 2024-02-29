+++
title = "Into (Rust)"
author = ["Gabriel Rosa"]
date = 2024-01-15T00:38:00-03:00
tags = ["rust", "conversion", "into"]
draft = false
+++

tags
: [Conversão (Rust)]({{< relref "conversao_rust.md" >}})

source
: [From and Into - Rust By Example](https://doc.rust-lang.org/stable/rust-by-example/conversion/from_into.html#into), [trait.Into - std::convert](https://doc.rust-lang.org/std/convert/trait.Into.html)

O `trait` `Into` tem basicamente a mesma função que o `From` e irá chamá-lo quando necessário.

Ele converte um valor para outro consumindo o valor de entrada.

Prefira utilizar o `From`.

```rust
use std::convert::Into;

#[derive(Debug)]
struct Number {
    value: i32,
}

impl Into<Number> for i32 {
    fn into(self) -> Number {
        Number { value: self }
    }
}

fn main() {
    let int = 5;
    let num: Number = int.into();
    println!("My number is {:?}", num);
}
```
