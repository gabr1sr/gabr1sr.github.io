+++
title = "Continue (Rust)"
author = ["Gabriel Rosa"]
date = 2024-02-26T21:46:00-03:00
tags = ["rust", "flow", "control", "continue", "loop"]
draft = false
+++

tags
: [Controle de Fluxo (Rust)]({{< relref "controle_de_fluxo_rust.md" >}})

source
: [break and continue](https://google.github.io/comprehensive-rust/control-flow-basics/break-continue.html), [continue expressions](https://doc.rust-lang.org/reference/expressions/loop-expr.html#continue-expressions)

A palavra-chave `continue` é utilizada quando queremos começar a próxima iteração imediatamente, dentro de um loop.

```rust
let mut i = 0;

loop {
    i += 1;

    if i > 5 {
        break;
    }

    if i % 2 == 0 {
        continue;
    }

    println!("{}", i);
}
```
