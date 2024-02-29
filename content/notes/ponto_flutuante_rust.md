+++
title = "Ponto Flutuante (Rust)"
author = ["Gabriel Rosa"]
date = 2023-11-14T05:14:00-03:00
tags = ["rust", "type", "primitive", "floating", "point"]
draft = false
+++

tags
: [Tipos Primitivos (Rust)]({{< relref "tipos_primitivos_rust.md" >}})

source
: [Primitives - Rust By Example](https://doc.rust-lang.org/rust-by-example/primitives.html), [Primitive Types - std Crate](https://doc.rust-lang.org/std/#primitives)

São números com casas decimais e que podem ser positivos ou negativos.

Os pontos flutuantes seguem o padrão IEEE 754-2008.


## Declaração {#declaração}

Diferentes formas que podemos declaras os números de ponto flutuante.


### Literal sem notação {#literal-sem-notação}

```rust
let float1: f32 = 1.1;
let float2: f64 = 2.2_001;

fn type_of<T>(_: &T) -> &'static str {
    std::any::type_name::<T>()
}

println!("float1: {} = {:?}", type_of(&float1), float1);
println!("float2: {} = {:?}", type_of(&float2), float2);
```


### Literal com notação científica {#literal-com-notação-científica}

```rust
let float1: f32 = 1.1e4;
let float2: f64 = 2.2_001e3;

fn type_of<T>(_: &T) -> &'static str {
    std::any::type_name::<T>()
}

println!("float1: {} = {:?}", type_of(&float1), float1);
println!("float2: {} = {:?}", type_of(&float2), float2);
```


### Literal com sufixo de tipo {#literal-com-sufixo-de-tipo}

```rust
let float1 = 1.1f32;
let float2 = 2.2_001e3f64;

fn type_of<T>(_: &T) -> &'static str {
    std::any::type_name::<T>()
}

println!("float1: {} = {:?}", type_of(&float1), float1);
println!("float2: {} = {:?}", type_of(&float2), float2);
```


## Limites {#limites}

Dígitos, valores mínimos e máximos:

```rust
println!("f32, {}, {:e}, {:e}", f32::DIGITS, f32::MIN, f32::MAX);
println!("f64, {}, {:e}, {:e}", f64::DIGITS, f64::MIN, f64::MAX);
```


## Códigos {#códigos}

<a id="code-snippet--show-results"></a>
```rust
fn type_of<T>(_: &T) -> &'static str {
    std::any::type_name::<T>()
}

println!("float1: {} = {:?}", type_of(&float1), float1);
println!("float2: {} = {:?}", type_of(&float2), float2);
```
