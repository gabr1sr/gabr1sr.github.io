+++
title = "Tuplas (Rust)"
author = ["Gabriel Rosa"]
date = 2023-11-14T07:02:00-03:00
draft = false
+++

tags
: [Tipos Primitivos (Rust)]({{< relref "tipos_primitivos_rust.md" >}})

source
: [Primitives - Rust By Example](https://doc.rust-lang.org/rust-by-example/primitives.html), [Primitive Types - std Crate](https://doc.rust-lang.org/std/#primitives)

É uma coleção de valores de diferentes tipos.

Tuplas são criadas usando `()`.

Sua assinatura de tipo é `(T1, T2, ...)`, onde `T1` e `T2` são os tipos dos membros da tupla.


## Declaração {#declaração}

Elas podem ser declaradas das seguintes formas:

<a id="code-snippet--long-tuple-declaration"></a>
```rust
let long_tuple = (1u8, 2u16, 3u32, 4u64, -1i8, -2i16, -3i32, -4i64, 0.1f32, 0.2f64, 'a', true);
```

<a id="code-snippet--tuple-of-tuples-declaration"></a>
```rust
let tuple_of_tuples = ((1u8, 2u16, 2u32), (4u64, -1i8), -2i16);
```

<a id="code-snippet--tuples-declaration"></a>
```rust
let long_tuple = (1u8, 2u16, 3u32, 4u64, -1i8, -2i16, -3i32, -4i64, 0.1f32, 0.2f64, 'a', true);
let tuple_of_tuples = ((1u8, 2u16, 2u32), (4u64, -1i8), -2i16);
let one_item_tuple = (5u32,);
```

```rust
let long_tuple = (1u8, 2u16, 3u32, 4u64, -1i8, -2i16, -3i32, -4i64, 0.1f32, 0.2f64, 'a', true);
let tuple_of_tuples = ((1u8, 2u16, 2u32), (4u64, -1i8), -2i16);
let one_item_tuple = (5u32,);
println!("Tupla longa: {:?}", long_tuple);
println!("Tupla de tuplas: {:?}", tuple_of_tuples);
println!("Tupla de 1 item: {:?}", one_item_tuple);
```

Podemos obter valores dessa tupla através do índice:

```rust
let long_tuple = (1u8, 2u16, 3u32, 4u64, -1i8, -2i16, -3i32, -4i64, 0.1f32, 0.2f64, 'a', true);
println!("Primeiro valor da tupla longa: {}", long_tuple.0);
println!("Segundo valor da tupla longa: {}", long_tuple.1);
```

Elas são printáveis, mas apenas se tiverem 12 ou menos elementos:

```rust
let tuple_of_tuples = ((1u8, 2u16, 2u32), (4u64, -1i8), -2i16);
println!("Tupla de tuplas: {:?}", tuple_of_tuples);
```

Elas podem ser usadas em funções:

```rust
fn reverse(pair: (i32, bool)) -> (bool, i32) {
    let (int_param, bool_param) = pair;

    (bool_param, int_param)
}

let pair = (1, true);

println!("Par: {:?}", pair);

println!("Par ao contrário: {:?}", reverse(pair));
```

Em structs:

```rust
#[derive(Debug)]
struct Matrix(f32, f32, f32, f32);

let matrix = Matrix(1.1, 1.2, 2.1, 2.2);

println!("{:?}", matrix);
```

E podemos desestruturar tuplas para criar associações:

```rust
let tuple = (1, "hello", 4.5, true);

println!("Tupla: {:?}", tuple);

let (a, b, c, d) = tuple;

println!("Valores separados: {:?}, {:?}, {:?}, {:?}", a, b, c, d);
```
