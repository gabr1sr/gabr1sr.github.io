+++
title = "For (Rust)"
author = ["Gabriel Rosa"]
date = 2024-02-26T18:10:00-03:00
tags = ["rust", "flow", "control", "for", "loop"]
draft = false
+++

tags
: [Controle de Fluxo (Rust)]({{< relref "controle_de_fluxo_rust.md" >}})

source
: [for](https://google.github.io/comprehensive-rust/pt-BR/control-flow-basics/loops/for.html), [for - Rust](https://doc.rust-lang.org/std/keyword.for.html), [Iterator loops](https://doc.rust-lang.org/reference/expressions/loop-expr.html#iterator-loops), [for and range - Rust By Example](https://doc.rust-lang.org/stable/rust-by-example/flow_control/for.html)

O for loop, ou loop de iterador, é usado para fazer looping em elementos providenciados pela implementação de `std::iter::IntoIterator`.

Se o iterador conseguir um valor, esse valor é comparado ao padrão irrefutável, o corpo do loop é executado e então o controle irá retornar ao início do loop for.

Se o iterador estiver vazio, a expressão for termina.

```rust
let v = &["apples", "cake", "coffe"];

for text in v {
    println!("I like {}.", text);
}
```

Usando range:

```rust
let mut sum = 0;

for n in 1..11 {
    sum += n;
}

println!("sum is {}", sum);
```
