+++
title = "Literais (Rust)"
author = ["Gabriel Rosa"]
date = 2024-01-13T16:07:00-03:00
tags = ["rust", "type", "literals"]
draft = false
+++

tags
: [Tipagem (Rust)]({{< relref "tipagem_rust.md" >}})

source
: [Literals - Rust By Example](https://doc.rust-lang.org/stable/rust-by-example/types/literals.html)

Literais numéricos podem ter anotações de tipo adicionando o tipo como sufixo.

```rust
let x = 1u8;
let y = 2u32;
let z = 3f32;

println!("size of `x` in bytes: {}", std::mem::size_of_val(&x));
println!("size of `y` in bytes: {}", std::mem::size_of_val(&y));
println!("size of `z` in bytes: {}", std::mem::size_of_val(&z));
```

O tipo dos literais numéricos sem sufixo de tipo depende de como eles são usados ([Inferência de Tipos (Rust)]({{< relref "inferencia_de_tipos_rust.md" >}})).

Se não existir nenhuma restrição, o compilador irá usar `i32` para inteiros e `f64` para pontos flutuantes.

```rust
let i = 1;
let f = 1.0;

println!("size of `i` in bytes: {}", std::mem::size_of_val(&i));
println!("size of `f` in bytes: {}", std::mem::size_of_val(&f));
```

Veja:

-   [Inteiros com Sinal (Rust)]({{< relref "inteiros_com_sinal_rust.md" >}})
-   [Inteiros sem Sinal (Rust)]({{< relref "inteiros_sem_sinal_rust.md" >}})
-   [Ponto Flutuante (Rust)]({{< relref "ponto_flutuante_rust.md" >}})
