+++
title = "Loop (Rust)"
author = ["Gabriel Rosa"]
date = 2024-02-26T18:20:00-03:00
draft = false
+++

tags
: [Controle de Fluxo (Rust)]({{< relref "controle_de_fluxo_rust.md" >}})

source
: [loop](https://google.github.io/comprehensive-rust/pt-BR/control-flow-basics/loops/loop.html), [Infinite loops](https://doc.rust-lang.org/reference/expressions/loop-expr.html#infinite-loops), [loop - Rust By Example](https://doc.rust-lang.org/stable/rust-by-example/flow_control/loop.html)

A palavra-chave `loop` é utilizada para criar loops infinitos.

Esses loops infinitos são executados para sempre ou até um `break` o interromper.

```rust
let mut i = 0;

loop {
    i += 1;
    println!("{i}");
    if i > 10 {
        break;
    }
}
```


## Rótulos {#rótulos}

Podemos colocar rótulos nesses loops:

```rust
'outer: loop {
    println!("Hello!");

    'inner: loop {
        println!("Hello again!");

        break 'outer;
    }
}
```
