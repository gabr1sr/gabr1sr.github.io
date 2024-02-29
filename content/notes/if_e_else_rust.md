+++
title = "If e Else (Rust)"
author = ["Gabriel Rosa"]
date = 2024-02-26T17:38:00-03:00
tags = ["rust", "flow", "control", "if", "else"]
draft = false
+++

tags
: [Controle de Fluxo (Rust)]({{< relref "controle_de_fluxo_rust.md" >}})

source
: [Condicionais](https://google.github.io/comprehensive-rust/pt-BR/control-flow-basics/conditionals.html), [if and if let expressions](https://doc.rust-lang.org/reference/expressions/if-expr.html#if-expressions), [if/else - Rust By Example](https://doc.rust-lang.org/stable/rust-by-example/flow_control/if_else.html)

Na linguagem Rust, podemos usar expressões if como em qualquer outra linguagem:


## If {#if}

```rust
fn main() {
    let x = 10;
    if x < 20 {
        println!("pequeno");
    } else if x < 100 {
        println!("grande");
    } else {
        println!("enorme");
    }
}
```

Também podemos usá-lo como uma expressão:

```rust
fn main() {
    let x = 10;
    let size = if x < 20 { "pequeno" } else { "grande" };
    println!("tamanho do número: {}", size);
}
```


## If Let {#if-let}

```rust
let dish = ("Ham", "Eggs");

if let ("Ham", eggs) = dish {
    println!("Ham is served with {}", eggs);
}

if let _ = 5 {
    println!("Irrefutable patterns are always true");
}
```
