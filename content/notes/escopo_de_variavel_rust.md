+++
title = "Escopo de Variável (Rust)"
author = ["Gabriel Rosa"]
date = 2024-03-05T23:15:00-03:00
draft = false
+++

tags
: [Ownership (Rust)]({{< relref "ownership_rust.md" >}}), [Escopo (Rust)]({{< relref "escopo_rust.md" >}})

source
: [What is Ownership? - The Rust Programming Language](https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html)

Vamos utilizar a seguinte instrução para referência:

```rust
let s = "hello";
```

Agora vamos colocá-la dentro de um bloco:

```rust
{                    // s ainda não é válido aqui, pois ainda não foi declarada
    let s = "hello"; // s é válido a partir deste ponto
}                    // o escopo acabou, então s não é mais válido
```

Quando `s` entra em cena, ela é válida.

Ela continua válida até que saia de cena.
