+++
title = "Expressões (Rust)"
author = ["Gabriel Rosa"]
date = 2024-02-26T17:25:00-03:00
draft = false
+++

tags
: [Rust]({{< relref "rust.md" >}})

source
: [Expressions - Rust By Example](https://doc.rust-lang.org/stable/rust-by-example/expression.html)

Um programa Rust é feito quase inteiramente de declarações.

```rust
fn main() {
    // statement
    // statement
    // statement
}
```

Existem alguns tipos de declarações em Rust. As duas mais comuns são:

-   [Associação de Variáveis (Rust)]({{< relref "associacao_de_variaveis_rust.md" >}})
-   Usar `;` com uma expressão

<!--listend-->

```rust
fn mani() {
    // variable binding
    let x = 5;

    // expression;
    x;
    x + 1;
    15;
}
```

Blocos também são expressões. Eles podem ser utilizados como valores durante a associação:

```rust
fn main() {
    let x = 5u32;

    let y = {
        let x_squared = x * x;
        let x_cube = x_squared * x;

        x_cube + x_squared + x
    };

    let z = {
        2 * x;
    };

    println!("x is {:?}", x);
    println!("y is {:?}", y);
    println!("z is {:?}", z);
}
```
