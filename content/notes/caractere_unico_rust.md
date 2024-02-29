+++
title = "Caractere Único (Rust)"
author = ["Gabriel Rosa"]
date = 2023-11-14T06:44:00-03:00
tags = ["rust", "type", "primitive", "char"]
draft = false
+++

tags
: [Tipos Primitivos (Rust)]({{< relref "tipos_primitivos_rust.md" >}})

source
: [Primitives - Rust By Example](https://doc.rust-lang.org/rust-by-example/primitives.html), [Primitive Types - std Crate](https://doc.rust-lang.org/std/#primitives)

É um valor escalar Unicode. Ou seja, seu valor pode ser de `0x000000` até `0x10FFFF`.

O valor não pode ser um ponto de código substituto (valor entre `0xD800` e `0xDFFF`).

Todos os `char` ocupam 4 bytes (32 bits).


## Declaração {#declaração}

Podemos declarar das seguintes formas:

```rust
let char1: char = 'A';
let char2: char = '\u{0042}';
let char3: char = char::from_u32(0x0043).unwrap();

println!("char1 = {:?}", char1);
println!("char2 = {:?}", char2);
println!("char3 = {:?}", char3);
```


## Códigos {#códigos}

<a id="code-snippet--show-results"></a>
```rust
println!("char1 = {:?}", char1);
println!("char2 = {:?}", char2);
println!("char3 = {:?}", char3);
```
