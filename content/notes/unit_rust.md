+++
title = "Unit (Rust)"
author = ["Gabriel Rosa"]
date = 2023-11-14T06:49:00-03:00
tags = ["rust", "type", "primitive", "unit"]
draft = false
+++

tags
: [Tipos Primitivos (Rust)]({{< relref "tipos_primitivos_rust.md" >}})

source
: [Primitives - Rust By Example](https://doc.rust-lang.org/rust-by-example/primitives.html), [Primitive Types - std Crate](https://doc.rust-lang.org/std/#primitives)

Tem exatamente um valor: `()`.

É usado quando não há nenhum valor que possa ser retornado.

É comumente visto de forma implícita, quando a função não tem um tipo de retorno especificado.

```rust
fn long() -> () {}

fn short() {}
```
