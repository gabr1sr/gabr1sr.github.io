+++
title = "Constantes (Rust)"
author = ["Gabriel Rosa"]
date = 2023-11-16T06:35:00-03:00
tags = ["rust", "type", "custom", "const"]
draft = false
+++

tags
: [Tipos Customizados (Rust)]({{< relref "tipos_customizados_rust.md" >}})

source
: [constants - Rust By Example](https://doc.rust-lang.org/rust-by-example/custom_types/constants.html)

Na linguagem Rust existem 2 tipos diferentes de constantes e ambas podem ser declaradas em qualquer escopo, incluindo o escopo global:

-   `const` =&gt; Um valor não alterável
-   `static` =&gt; Um valor que tem a possibilidade de ser mutável e que tem a lifetime `'static`. Porém, alterar seu valor é `unsafe`.


## Declaração {#declaração}

Podemos declarar as constantes da seguinte forma:

```rust
static LANGUAGE: &str = "Rust";
const THRESHOLD: i32 = 10;

println!("Linguagem: {}", LANGUAGE);
println!("Threshold: {}", THRESHOLD);
```
