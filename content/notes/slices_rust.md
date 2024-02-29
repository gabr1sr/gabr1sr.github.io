+++
title = "Slices (Rust)"
author = ["Gabriel Rosa"]
date = 2023-11-15T17:39:00-03:00
tags = ["rust", "type", "primitive", "slice"]
draft = false
+++

tags
: [Tipos Primitivos (Rust)]({{< relref "tipos_primitivos_rust.md" >}})

source
: [Primitives - Rust By Example](https://doc.rust-lang.org/rust-by-example/primitives.html), [Primitive Types - std Crate](https://doc.rust-lang.org/std/#primitives), [The Slice Type - The Rust Programming Language](https://doc.rust-lang.org/book/ch04-03-slices.html), [Arrays and Slices - Rust By Example](https://doc.rust-lang.org/rust-by-example/primitives/array.html)

Slices são um tipo que permitem referenciar uma sequência contígua de elementos em uma coleção ao invés de referenciar a coleção inteira.

Sua assinatura de tipo é: `&[T]`.


## Declaração {#declaração}

Quando queremos obter parte de uma string ou array, podemos especificar o range de quais elementos queremos obter dessa coleção.

Exemplos:


### Slice de String {#slice-de-string}

Temos uma String `"Hello World"` e queremos dividi-la em 2 slices:

-   `hello` =&gt; um slice contendo a palavra `"Hello"`
-   `world` =&gt; outro slice contendo a palavra `"World"`

Podemos fazer isto desta forma:

```rust
let s = String::from("Hello World");
let hello = &s[0..5];
let world = &s[6..11];

println!("s = {:?}", s);
println!("hello = {:?}", hello);
println!("world = {:?}", world);
```

Podemos também criar um slice de string de forma direta:

```rust
let slice1 = "Hello, World!";

println!("slice1 = {:?}", slice1);
```


### Slice de Array {#slice-de-array}

Temos um array `[1, 2, 3, 4, 5]` e queremos dividi-lo em 2 slices:

-   `y` =&gt; um slice contendo os elementos `[1, 2, 3]`
-   `z` =&gt; outro slice contendo os elementos `[4, 5]`

Realizamos esta ação assim:

```rust
let xs: [i32; 5] = [1, 2, 3, 4, 5];
let y = &xs[..3];
let z = &xs[3..];

println!("xs = {:?}", xs);
println!("y = {:?}", y);
println!("z = {:?}", z);
```

Podemos também criar um slice de array de forma direta:

```rust
let slice1 = &[2, 3];

println!("slice1 = {:?}", slice1);
```


## Ranges {#ranges}

Os ranges podem ser especificados utilizando a síntaxe de range `..` para definir quais elementos da coleção estarão no slice.


### De um ponto específico até outro ponto específico {#de-um-ponto-específico-até-outro-ponto-específico}

Se quisermos pegar o elemento da posição `x` até a posição `y` de uma coleção (`&[x..y]`), fazemos da seguinte forma:

```rust
let collection = String::from("Hello World!");

let x = 0;
let y = 5;

let slice1 = &collection[x..y];

println!("collection = {:?}", collection);
println!("slice1 = {:?}", slice1);
```


### De um ponto específico até o final {#de-um-ponto-específico-até-o-final}

Se quisermos pegar o elemento da posição `x` até a posição final de uma coleção (`&[x..]`), fazemos da seguinte forma:

```rust
let collection = String::from("Hello World!");

let x = 6;

let slice1 = &collection[x..];

println!("collection = {:?}", collection);
println!("slice1 = {:?}", slice1);
```


### Do começo até um ponto específico {#do-começo-até-um-ponto-específico}

Se quisermos pegar o elemento da posição inicial até a posição `x` de uma coleção (`&[..x]`), fazemos da seguinte forma:

```rust
let collection = String::from("Hello World!");

let x = 5;

let slice1 = &collection[..x];

println!("collection = {:?}", collection);
println!("slice1 = {:?}", slice1);
```


## Códigos {#códigos}

<a id="code-snippet--show-string-results"></a>
```rust
println!("s = {:?}", s);
println!("hello = {:?}", hello);
println!("world = {:?}", world);
```

<a id="code-snippet--show-array-results"></a>
```rust
println!("xs = {:?}", xs);
println!("y = {:?}", y);
println!("z = {:?}", z);
```

<a id="code-snippet--show-results"></a>
```rust
println!("collection = {:?}", collection);
println!("slice1 = {:?}", slice1);
```
