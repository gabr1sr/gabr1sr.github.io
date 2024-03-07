+++
title = "Macros (Rust)"
author = ["Gabriel Rosa"]
date = 2024-02-29T22:11:00-03:00
tags = ["rust", "macros"]
draft = false
+++

tags
: [Rust]({{< relref "rust.md" >}})

source
: [Macros - Comprehensive Rust](https://google.github.io/comprehensive-rust/control-flow-basics/macros.html), [Macros - The Rust Reference](https://doc.rust-lang.org/reference/macros.html), [Macros By Example - The Rust Reference](https://doc.rust-lang.org/reference/macros-by-example.html), [Macros - The Rust Programming Language](https://doc.rust-lang.org/book/ch19-06-macros.html)

Macros são uma forma de escrever código que escreve outros códigos. Ou seja, meta-programação.

Na linguagem Rust, as macros podem ser identificadas por nomes terminados em `!`.

Exemplos de macros:

-   `println!` =&gt; imprime uma linha para a standard output, aplicando a formatação desejada.
-   `format!` =&gt; funciona como o `println!`, mas retorna o resultado como `String`.
-   `dbg!` =&gt; faz logging do valor da expressão e retorna ela.
-   `todo!` =&gt; marca parte do código como não implementada ainda. Se executado irá dar panic.
-   `unreachable!` =&gt; marca parte do código como não alcançável.Se executado irá dar panic.
-   `vec!` =&gt; Cria um `Vec` a partir de uma expressão.


## Macros Declarativas {#macros-declarativas}

A forma mais utilizada de macros em Rust são as macros declarativas.

Elas também são chamadas de _macros by example_, `macro_rules!` _macros_, ou apenas _macros_.

Elas permitem você declarar macros de forma similar a uma expressão `match`.

Para definir uma macro, você utiliza `macro_rules!`.

Vamos pegar como exemplo a macro `vec!`. Nós utilizamos ela desta forma:

```rust
let v: Vec<u32> = vec![1, 2, 3];
```

Se formos definir ela utilizando `macro_rules!`, sua declaração será como esta:

```rust
#[macro_export]
macro_rules! vec {
    ( $( $x:expr ),* ) => {
        {
            let mut temp_vec = Vec::new();
            $(
                temp_vec.push($x);
            )*
            temp_vec
        }
    };
}
```
