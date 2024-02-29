+++
title = "Estruturas (Rust)"
author = ["Gabriel Rosa"]
date = 2023-11-16T01:11:00-03:00
tags = ["rust", "type", "custom", "struct"]
draft = false
+++

tags
: [Tipos Customizados (Rust)]({{< relref "tipos_customizados_rust.md" >}})

source
: [Structures - Rust By Example](https://doc.rust-lang.org/rust-by-example/custom_types/structs.html)

Na linguagem Rust, existem 3 tipos de estruturas:

-   Estruturas-tuplas
-   Estruturas C
-   Estruturas unit


## Declaração {#declaração}

Formas diferentes de declaração de estruturas.


### Estruturas-tuplas {#estruturas-tuplas}

São tuplas nomeadas que podem ser definidas desta forma:

```rust
struct Pair(i32, f32);
```


### Estruturas C {#estruturas-c}

São estruturas comuns que podem ser definidas da seguinte forma:

<a id="code-snippet--c-structures"></a>
```rust
#![allow(dead_code)]

#[derive(Debug, Clone, Copy)]
struct Point {
    x: f32,
    y: f32,
}

#[derive(Debug)]
struct Rectangle {
    top_left: Point,
    bottom_right: Point,
}
```


### Estruturas Unit {#estruturas-unit}

São estruturas vazias, sem campos, geralmente utilizadas para polimorfismo (generics):

```rust
struct Unit;
```


## Instanciação {#instanciação}

As estruturas podem ser instanciadas das seguintes formas:


### Instanciação padrão {#instanciação-padrão}

<a id="code-snippet--default-struct-initialize"></a>
```rust
#![allow(dead_code)]

#[derive(Debug, Clone, Copy)]
struct Point {
    x: f32,
    y: f32,
}

#[derive(Debug)]
struct Rectangle {
    top_left: Point,
    bottom_right: Point,
}

let point: Point = Point { x: 10.3, y: 0.4 };

println!("point = {:?}", point);
```


### Instanciação curta {#instanciação-curta}

```rust
#![allow(dead_code)]

#[derive(Debug, Clone, Copy)]
struct Point {
    x: f32,
    y: f32,
}

#[derive(Debug)]
struct Rectangle {
    top_left: Point,
    bottom_right: Point,
}

let x = 10.5;
let y = 0.7;

let point: Point = Point { x, y };

println!("point = {:?}", point);
```


### Instanciação usando campos de outra estrutura {#instanciação-usando-campos-de-outra-estrutura}

```rust
#![allow(dead_code)]

#[derive(Debug, Clone, Copy)]
struct Point {
    x: f32,
    y: f32,
}

#[derive(Debug)]
struct Rectangle {
    top_left: Point,
    bottom_right: Point,
}

let point: Point = Point { x: 10.3, y: 0.4 };

let bottom_right = Point { x: 5.2, ..point };

println!("point = {:?}", point);

println!("bottom_right = {:?}", bottom_right);
```


### Instanciando dentro de outra instanciação de estrutura {#instanciando-dentro-de-outra-instanciação-de-estrutura}

```rust
#![allow(dead_code)]

#[derive(Debug, Clone, Copy)]
struct Point {
    x: f32,
    y: f32,
}

#[derive(Debug)]
struct Rectangle {
    top_left: Point,
    bottom_right: Point,
}

let point: Point = Point { x: 10.3, y: 0.4 };

let bottom_right = Point { x: 5.2, ..point };

let rectangle: Rectangle = Rectangle {
    top_left: Point { x: 10.3, y: 0.4 },
    bottom_right: bottom_right,
};

println!("point = {:?}", point);

println!("bottom_right = {:?}", bottom_right);

println!("rectangle = {:?}", rectangle);
```


## Valores {#valores}

Podemos obter os valores das seguintes formas:


### Forma padrão {#forma-padrão}

```rust
#![allow(dead_code)]

#[derive(Debug, Clone, Copy)]
struct Point {
    x: f32,
    y: f32,
}

#[derive(Debug)]
struct Rectangle {
    top_left: Point,
    bottom_right: Point,
}

let point: Point = Point { x: 10.4, y: 0.4 };

println!("x = {}, y = {}", point.x, point.y);
```


### Desestruturação {#desestruturação}

```rust
#![allow(dead_code)]

#[derive(Debug, Clone, Copy)]
struct Point {
    x: f32,
    y: f32,
}

#[derive(Debug)]
struct Rectangle {
    top_left: Point,
    bottom_right: Point,
}

let point: Point = Point { x: 10.4, y: 0.4 };

let Point { x: left_edge, y: right_edge } = point;

println!("left_edge = {}, right_edge = {}", left_edge, right_edge);

let Point { x, y } = point;

println!("x = {}, y = {}", x, y);
```


## Códigos {#códigos}

<a id="code-snippet--show-point-results"></a>
```rust
println!("point = {:?}", point);
```

<a id="code-snippet--show-point-bottom-right-results"></a>
```rust
println!("point = {:?}", point);

println!("bottom_right = {:?}", bottom_right);
```

<a id="code-snippet--show-results"></a>
```rust
println!("point = {:?}", point);

println!("bottom_right = {:?}", bottom_right);

println!("rectangle = {:?}", rectangle);
```
