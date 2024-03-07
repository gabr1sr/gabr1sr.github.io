+++
title = "Ownership (Rust)"
author = ["Gabriel Rosa"]
date = 2024-03-05T04:26:00-03:00
tags = ["rust", "ownership"]
draft = false
+++

tags
: [Rust]({{< relref "rust.md" >}})

source
: [Understanding Onwership - The Rust Programming Language](https://doc.rust-lang.org/book/ch04-00-understanding-ownership.html), [What is Ownership? - The Rust Programming Language](https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html)

É a forma com que a linguagem Rust garante segurança de memória sem precisar de um garbage collector.

A memória é gerenciada através de um sistema de ownership com um conjunto de regras que o compialdor checa. Se alguma dessas regras são violadas, o programa não irá compilar.


## Regras de Ownership {#regras-de-ownership}

-   Cada valor tem um dono.
-   Só pode haver um dono por vez.
-   Quando o dono sai de cena, ele será descartado.


## Assuntos {#assuntos}

-   [Heap (Rust)]({{< relref "heap_rust.md" >}})
-   [Stack (Rust)]({{< relref "stack_rust.md" >}})
-   [Escopo de Variável (Rust)]({{< relref "escopo_de_variavel_rust.md" >}})
-   [Referências (Rust)]({{< relref "referencias_rust.md" >}})
