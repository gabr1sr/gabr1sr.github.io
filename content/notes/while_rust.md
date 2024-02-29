+++
title = "While (Rust)"
author = ["Gabriel Rosa"]
date = 2024-02-26T17:44:00-03:00
draft = false
+++

tags
: [Controle de Fluxo (Rust)]({{< relref "controle_de_fluxo_rust.md" >}})

source
: [Loops](https://google.github.io/comprehensive-rust/pt-BR/control-flow-basics/loops.html), [while - Rust By Example](https://doc.rust-lang.org/stable/rust-by-example/flow_control/while.html), [Loop expressions](https://doc.rust-lang.org/reference/expressions/loop-expr.html#predicate-loops)

Podemos utilizar a palavra-chave `while` para criar loops predicados.

O corpo do loop será executado enquanto a condição for verdadeira.


## Loop predicado {#loop-predicado}

```rust
let mut i = 0;

while i < 10 {
    println!("hello");
    i = i + 1;
}
```


## Loop predicado com pattern {#loop-predicado-com-pattern}

```rust
let mut x = vec![1, 2, 3];

while let Some(y) = x.pop() {
    println!("y = {}", y);
}

while let _ = 5 {
    println!("Irrefutable patterns are always true");
    break;
}
```
