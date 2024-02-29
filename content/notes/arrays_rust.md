+++
title = "Arrays (Rust)"
author = ["Gabriel Rosa"]
date = 2023-11-14T08:20:00-03:00
tags = ["rust", "type", "primitive", "array"]
draft = false
+++

tags
: [Tipos Primitivos (Rust)]({{< relref "tipos_primitivos_rust.md" >}})

source
: [Primitives - Rust By Example](https://doc.rust-lang.org/rust-by-example/primitives.html), [Arrays and Slices - Rust By Example](https://doc.rust-lang.org/rust-by-example/primitives/array.html), [Primitive Types - std Crate](https://doc.rust-lang.org/std/#primitives)

Podemos dizer que os arrays são coleções de objetos do mesmo tipo `T`.

Arrays podem ser criados utilizando `[]`.

Seu tamanho é obtido em tempo de compilação.

Assinatura de tipo: `[T; length]`.


## Declaração {#declaração}

Podemos declarar arrays das seguintes formas:


### Array de tamanho fixo {#array-de-tamanho-fixo}

```rust
let xs: [i32; 5] = [1, 2, 3, 4, 5];

println!("xs[0] = {}", xs[0]);
println!("xs[1] = {}", xs[1]);
println!("xs.len() = {}", xs.len());
println!("xs ocupa {} bytes", std::mem::size_of_val(&xs));
```


### Array de elementos inicializados com mesmo valor {#array-de-elementos-inicializados-com-mesmo-valor}

```rust
let xs: [i32; 500] = [0; 500];

println!("xs[0] = {}", xs[0]);
println!("xs[1] = {}", xs[1]);
println!("xs.len() = {}", xs.len());
println!("xs ocupa {} bytes", std::mem::size_of_val(&xs));
```


## Códigos {#códigos}

<a id="code-snippet--show-results"></a>
```rust
println!("xs[0] = {}", xs[0]);
println!("xs[1] = {}", xs[1]);
println!("xs.len() = {}", xs.len());
println!("xs ocupa {} bytes", std::mem::size_of_val(&xs));
```
