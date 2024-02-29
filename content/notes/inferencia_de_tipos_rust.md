+++
title = "Inferência de Tipos (Rust)"
author = ["Gabriel Rosa"]
date = 2023-11-12T00:00:00-03:00
tags = ["rust", "type", "inference"]
draft = false
+++

tags
: [Tipagem (Rust)]({{< relref "tipagem_rust.md" >}})

source
: [Primitives - Rust By Example](https://doc.rust-lang.org/rust-by-example/primitives.html), [Inference - Rust By Example](https://doc.rust-lang.org/rust-by-example/types/inference.html)

A inferência de tipos, na linguagem Rust, acontece quando você declara uma variável e o tipo dela é deduzido conforme ela é utilizada no seu código.

Exemplo:

```rust-ts
let mut inferred_type = 12;

// ...

inferred_type = 4294967296i64;
```

Podemos observar que não definimos o tipo da variável `inferred_type` em sua declaração.

Como mais abaixo alteramos seu valor para `4294967296` e declaramos o tipo através de sufixo `i64`, a variável não será declarada com o tipo padrão para números inteiros (`i32`), mas sim o tipo `i64` que foi inferido de algumas linhas abaixo da declaração da variável.
