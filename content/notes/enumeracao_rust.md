+++
title = "Enumeração (Rust)"
author = ["Gabriel Rosa"]
date = 2023-11-16T04:34:00-03:00
tags = ["rust", "type", "custom", "enum"]
draft = false
+++

tags
: [Tipos Customizados (Rust)]({{< relref "tipos_customizados_rust.md" >}})

source
: [Enums - Rust By Example](https://doc.rust-lang.org/rust-by-example/custom_types/enum.html)


## Declaração {#declaração}

Podemos declaras as enumerações das seguintes formas:


### Enumeração padrão {#enumeração-padrão}

```rust
enum WebEvent {
    PageLoad,
    PageUnload,
}

let load = WebEvent::PageLoad;
let unload = WebEvent::PageUnload;
```


### Enumeração com tuplas {#enumeração-com-tuplas}

```rust
enum WebEvent {
    KeyPress(char),
    Paste(String),
}

let pressed = WebEvent::KeyPress('x');
let pasted = WebEvent::Paste("hello".to_owned());
```


### Enumeração com structs {#enumeração-com-structs}

```rust
enum WebEvent {
    Click { x: i64, y: i64 },
}

let click = WebEvent::Click { x: 20, y: 80 };
```


### Enumeração C-like {#enumeração-c-like}

```rust
enum Color {
    Red = 0xff0000,
    Green = 0x00ff00,
    Blue = 0x0000ff,
}

let red = Color::Red;
let green = Color::Green;
let blue = Color::Blue;
```


## Alias {#alias}

Podemos criar um apelido (alias) para um `enum` utilizando a palavra-chave `type`:

```rust
enum VeryVerboseEnumOfThingsToDoWithNumbers {
    Add,
    Subtract,
}

type Operations = VeryVerboseEnumOfThingsToDoWithNumbers;

let x = Operations::Add;
```

Porém, a forma mais comum, é vermos um alias dentro de blocos `impl` como `Self`:

```rust
enum VeryVerboseEnumOfThingsToDoWithNumbers {
    Add,
    Subtract,
}

impl VeryVerboseEnumOfThingsToDoWithNumbers {
    fn run(&self, x: i32, y: i32) -> i32 {
        match self {
            Self::Add => x + y,
            Self::Subtract => x - y,
        }
    }
}
```


## Use {#use}

Podemos utilizar valores de enumerações diretamente, sem precisar chamar seu escopo, utilizando a palavra-chave `use`:

```rust
enum Status {
    Rich,
    Poor,
}

use crate::Status::{Poor, Rich};

let poor = Poor;
let rich = Rich;
```

Ou dessa forma:

```rust
enum Status {
    Rich,
    Poor,
}

use crate::Status::*;

let poor = Poor;
let rich = Rich;
```
