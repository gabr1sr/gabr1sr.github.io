+++
title = "Break (Rust)"
author = ["Gabriel Rosa"]
date = 2024-02-26T21:42:00-03:00
draft = false
+++

tags
: [Controle de Fluxo (Rust)]({{< relref "controle_de_fluxo_rust.md" >}})

source
: [break and continue](https://google.github.io/comprehensive-rust/control-flow-basics/break-continue.html), [break expressions](https://doc.rust-lang.org/reference/expressions/loop-expr.html#break-expressions)

A palavra-chave `break` é utilizada para interromper a execução do corpo de um loop.

```rust
let mut last = 0;
for x in 1..100 {
    if x > 12 {
        break;
    }
    last = x;
}

println!("{last}");
```

Pode também ser usado em conjunto com rótulos:

```rust
'outer: loop {
    while true {
        break 'outer;
    }
}
```

Ou parar a execução do corpo de algum e retornar valores:

```rust
let result = 'block: {
    if 1 > 2 {
        break 'block 1;
    }

    if 2 > 1 {
        break 'block 2;
    }

    3
};

println!("{result}");
```
