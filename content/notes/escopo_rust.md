+++
title = "Escopo (Rust)"
author = ["Gabriel Rosa"]
date = 2024-01-08T16:44:00-03:00
tags = ["rust", "scope"]
draft = false
+++

tags
: [Rust]({{< relref "rust.md" >}})

source
: [Scope and Shadowing - Rust By Example (Book)](https://doc.rust-lang.org/stable/rust-by-example/variable_bindings/scope.html)

Toda [Associação de Variáveis]({{< relref "associacao_de_variaveis_rust.md" >}}) tem um escopo e é restringida a viver em um bloco.

Um bloco é uma coleção de declarações que estão dentro de `{}`.

```rust
fn main() {
    let long_lived_binding = 1;

    {
        let short_lived_binding = 2;
        println!("inner short: {}", short_lived_binding);
    }

    // ERRO:
    // println!("outer short: {}", short_lived_binding);

    println!("outer long: {}", long_lived_binding);
}
```
