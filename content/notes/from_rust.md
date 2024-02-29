+++
title = "From (Rust)"
author = ["Gabriel Rosa"]
date = 2024-01-15T00:32:00-03:00
tags = ["rust", "conversion", "from"]
draft = false
+++

tags
: [Conversão (Rust)]({{< relref "conversao_rust.md" >}})

source
: [From and Into - Rust By Example](https://doc.rust-lang.org/stable/rust-by-example/conversion/from_into.html#from), [trait.From - std::convert](https://doc.rust-lang.org/std/convert/trait.From.html)

O `From` é um `trait` que define como um tipo pode criar ele mesmo através de outro tipo.

Ele converte um valor para outro enquanto consume o valor de entrada.

É preferível usar `From` do que `Into`.


## Exemplo {#exemplo}

```rust
let my_str = "hello";
let my_string = String::from(my_str);
println!("{}", my_string);
```


## Implementação {#implementação}

```rust
use std::convert::From;

#[derive(Debug)]
struct Number {
    value: i32,
}

impl From<i32> for Number {
    fn from(item: i32) -> Self {
        Number { value: item }
    }
}

fn main() {
    let num = Number::from(30);
    println!("My number is {:?}", num);
}
```
