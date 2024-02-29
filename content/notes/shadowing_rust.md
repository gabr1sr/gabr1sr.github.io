+++
title = "Shadowing (Rust)"
author = ["Gabriel Rosa"]
date = 2023-11-12T00:04:00-03:00
tags = ["rust", "var", "shadowing"]
draft = false
+++

tags
: [Variáveis (Rust)]({{< relref "associacao_de_variaveis_rust.md" >}})

source
: [Primitives - Rust by Example](https://doc.rust-lang.org/rust-by-example/primitives.html)

Quando declaramos uma variável imutável e queremos alterar seu valor e/ou seu tipo, podemos utilizar a técnica de shadowing para reescrever seu valor:

```rust
let mut value = 12; // i32

println!("value: {:?}", value);

value = 45;

println!("value: {:?}", value);

let value = true;   // bool

println!("value: {:?}", value);
```
