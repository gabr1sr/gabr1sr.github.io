+++
title = "Freezing (Rust)"
author = ["Gabriel Rosa"]
date = 2023-11-16T06:47:00-03:00
tags = ["rust", "var", "freezing"]
draft = false
+++

tags
: [Variáveis (Rust)]({{< relref "associacao_de_variaveis_rust.md" >}})

source
: [Freezing - Rust By Example](https://doc.rust-lang.org/rust-by-example/variable_bindings/freeze.html)

Freezing é a técnica de sobrescrever uma variável mutável com uma variável imutável em outro escopo, fazendo com que ela não possa ser modificada naquele escopo.


## Como Usar {#como-usar}

Podemos fazer freezing da seguinte forma:

```rust
let mut data = 123;

println!("data = {}", data);

// outro escopo
{
    let data = 456;
    // neste escopo, data não poderá mais ser alterado

    println!("data = {}", data);
}

// porém, neste escopo, que foi declarada como mutável, ela ainda poderá ser alterada
data = 789;

println!("data = {}", data);
```
