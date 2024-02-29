+++
title = "Inteiros com Sinal (Rust)"
author = ["Gabriel Rosa"]
date = 2023-11-14T05:07:00-03:00
tags = ["rust", "type", "primitive", "signed", "integer"]
draft = false
+++

tags
: [Tipos Primitivos (Rust)]({{< relref "tipos_primitivos_rust.md" >}})

source
: [Primitives - Rust By Example](https://doc.rust-lang.org/rust-by-example/primitives.html), [Primitive Types - std Crate](https://doc.rust-lang.org/std/#primitives)

São números inteiros que podem ser positivos ou negativos.


## Declaração {#declaração}

Diferentes formas que podemos declarar os números inteiros com sinal.


### Literal sem notação {#literal-sem-notação}

```rust
let num1: i8 = -123;
let num2: i16 = 456;
let num3: i32 = -789;
let num4: i64 = 800000;
let num5: i128 = -160_000_000;
let num6: isize = 888;

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
let num1: i8 = 0x7F;
let num2: i16 = -0x7FFF;
let num3: i32 = 0x7FFFFFFF;
let num4: i64 = -0x7FFFFFFFFFFFFFFF;
let num5: i128 = 0x7FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF;
let num6: isize = -0x7FFFFFFF;

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
let num1: i8 = -0b01;
let num2: i16 = 0b10;
let num3: i32 = -0b11;
let num4: i64 = 0b100;
let num5: i128 = -0b101;
let num6: isize = 0b110;

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
let num1: i8 = 0o001;
let num2: i16 = -0o002;
let num3: i32 = 0o004;
let num4: i64 = -0o006;
let num5: i128 = 0o0012;
let num6: isize = -0o024;

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
let num1 = -1i8;
let num2 = 0x02i16;
let num3 = -0b11i32;
let num4 = 0o52i64;
let num5 = -100_000i128;
let num6 = 0x123123isize;

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
println!("i8, {:e}, {:e}", i8::MIN, i8::MAX);
println!("i16, {:e}, {:e}", i16::MIN, i16::MAX);
println!("i32, {:e}, {:e}", i32::MIN, i32::MAX);
println!("i64, {:e}, {:e}", i64::MIN, i64::MAX);
println!("i128, {:e}, {:e}", i128::MIN, i128::MAX);
println!("isize, {:e}, {:e}", isize::MIN, isize::MAX);
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
