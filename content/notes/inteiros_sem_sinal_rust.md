+++
title = "Inteiros sem Sinal (Rust)"
author = ["Gabriel Rosa"]
date = 2023-11-14T05:11:00-03:00
tags = ["rust", "type", "primitive", "unsigned", "integer"]
draft = false
+++

tags
: [Tipos Primitivos (Rust)]({{< relref "tipos_primitivos_rust.md" >}})

source
: [Primitives - Rust By Example](https://doc.rust-lang.org/rust-by-example/primitives.html), [Primitive Types - std Crate](https://doc.rust-lang.org/std/#primitives)

São números inteiros que podem ser apenas positivos.


## Declaração {#declaração}

Diferentes formas que podemos declarar os números inteiros sem sinal.


### Literal sem notação {#literal-sem-notação}

```rust
let num1: u8 = 123;
let num2: u16 = 456;
let num3: u32 = 789;
let num4: u64 = 800000;
let num5: u128 = 160_000_000;
let num6: usize = 888;

fn type_of<T>(_: &T) -> &'static str {
    std::any::type_name::<T>()
}

println!("num1: {} = {:?}", type_of(&num1), num1);
println!("num2: {} = {:?}", type_of(&num2), num2);
println!("num3: {} = {:?}", type_of(&num3), num3);
println!("num4: {} = {:?}", type_of(&num4), num4);
println!("num5: {} = {:?}", type_of(&num5), num5);
println!("num6: {} = {:?}", type_of(&num6), num6);
```


### Literal com notação hexadecimal {#literal-com-notação-hexadecimal}

```rust
let num1: u8 = 0xFF;
let num2: u16 = 0xFFFF;
let num3: u32 = 0xFFFFFFFF;
let num4: u64 = 0xFFFFFFFFFFFFFFFF;
let num5: u128 = 0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF;
let num6: usize = 0xFFFFFFFF;

fn type_of<T>(_: &T) -> &'static str {
    std::any::type_name::<T>()
}

println!("num1: {} = {:?}", type_of(&num1), num1);
println!("num2: {} = {:?}", type_of(&num2), num2);
println!("num3: {} = {:?}", type_of(&num3), num3);
println!("num4: {} = {:?}", type_of(&num4), num4);
println!("num5: {} = {:?}", type_of(&num5), num5);
println!("num6: {} = {:?}", type_of(&num6), num6);
```


### Literal com notação binária {#literal-com-notação-binária}

```rust
let num1: u8 = 0b01;
let num2: u16 = 0b10;
let num3: u32 = 0b11;
let num4: u64 = 0b100;
let num5: u128 = 0b101;
let num6: usize = 0b110;

fn type_of<T>(_: &T) -> &'static str {
    std::any::type_name::<T>()
}

println!("num1: {} = {:?}", type_of(&num1), num1);
println!("num2: {} = {:?}", type_of(&num2), num2);
println!("num3: {} = {:?}", type_of(&num3), num3);
println!("num4: {} = {:?}", type_of(&num4), num4);
println!("num5: {} = {:?}", type_of(&num5), num5);
println!("num6: {} = {:?}", type_of(&num6), num6);
```


### Literal com notação binária {#literal-com-notação-binária}

```rust
let num1: u8 = 0o001;
let num2: u16 = 0o002;
let num3: u32 = 0o004;
let num4: u64 = 0o006;
let num5: u128 = 0o0012;
let num6: usize = 0o024;

fn type_of<T>(_: &T) -> &'static str {
    std::any::type_name::<T>()
}

println!("num1: {} = {:?}", type_of(&num1), num1);
println!("num2: {} = {:?}", type_of(&num2), num2);
println!("num3: {} = {:?}", type_of(&num3), num3);
println!("num4: {} = {:?}", type_of(&num4), num4);
println!("num5: {} = {:?}", type_of(&num5), num5);
println!("num6: {} = {:?}", type_of(&num6), num6);
```


### Literal com sufixo de tipo {#literal-com-sufixo-de-tipo}

```rust
let num1 = 1u8;
let num2 = 0x02u16;
let num3 = 0b11u32;
let num4 = 0o52u64;
let num5 = 100_000u128;
let num6 = 0x123123usize;

fn type_of<T>(_: &T) -> &'static str {
    std::any::type_name::<T>()
}

println!("num1: {} = {:?}", type_of(&num1), num1);
println!("num2: {} = {:?}", type_of(&num2), num2);
println!("num3: {} = {:?}", type_of(&num3), num3);
println!("num4: {} = {:?}", type_of(&num4), num4);
println!("num5: {} = {:?}", type_of(&num5), num5);
println!("num6: {} = {:?}", type_of(&num6), num6);
```


## Limites {#limites}

Valores mínimos e máximos:

```rust
println!("u8, {:e}, {:e}", u8::MIN, u8::MAX);
println!("u16, {:e}, {:e}", u16::MIN, u16::MAX);
println!("u32, {:e}, {:e}", u32::MIN, u32::MAX);
println!("u64, {:e}, {:e}", u64::MIN, u64::MAX);
println!("u128, {:e}, {:e}", u128::MIN, u128::MAX);
println!("usize, {:e}, {:e}", usize::MIN, usize::MAX);
```


## Códigos {#códigos}

<a id="code-snippet--show-results"></a>
```rust
fn type_of<T>(_: &T) -> &'static str {
    std::any::type_name::<T>()
}

println!("num1: {} = {:?}", type_of(&num1), num1);
println!("num2: {} = {:?}", type_of(&num2), num2);
println!("num3: {} = {:?}", type_of(&num3), num3);
println!("num4: {} = {:?}", type_of(&num4), num4);
println!("num5: {} = {:?}", type_of(&num5), num5);
println!("num6: {} = {:?}", type_of(&num6), num6);
```
