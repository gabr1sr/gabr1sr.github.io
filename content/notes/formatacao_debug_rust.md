+++
title = "Formatação Debug (Rust)"
author = ["Gabriel Rosa"]
date = 2023-11-13T06:56:00-03:00
tags = ["rust", "macro", "format", "debug"]
draft = false
+++

tags
: [Formatação (Rust)]({{< relref "formatacao_rust.md" >}})

source
: [Formatted print - Rust By Example](https://doc.rust-lang.org/rust-by-example/hello/print.html), [Debug - Rust By Example](https://doc.rust-lang.org/rust-by-example/hello/print/print_debug.html), [std::fmt Module](https://doc.rust-lang.org/std/fmt/), [std::fmt::Debug Trait](https://doc.rust-lang.org/std/fmt/trait.Debug.html)

É o `trait` da `std::fmt` utilizado para depuração.

Todos os tipos que quiserem ser impressos usando depuração devem ter uma implementação para `fmt::Debug`.

Ou simplesmente utilizar `derive` para automaticamente criar uma implementação.

Os tipos da `std` já têm essa implementação, com exceção do `struct`.


## Flags {#flags}

-   `?` =&gt; Depuração padrão
-   `#?` =&gt; Depuração mais elegante (pretty-printing)
-   `x?` =&gt; Depuração com inteiros hexadecimais em minúsculo
-   `X?` =&gt; Depuração com inteiros hexadecimais em maiúsculo


## Como Usar {#como-usar}

Para os tipos que já têm essa implementação, você pode utilizar da seguinte forma:

```rust
fn main() {
    let value: i32 = 45;

    println!("Debug '?' {:?}", value);
    println!("Debug '#?' {:#?}", value);
    println!("Debug 'x?' {:x?}", value);
    println!("Debug 'X?' {:X?}", value);
}
```

Para os tipos que não têm essa implementação, como o `struct`, por exemplo, podemos fazer isto:

```rust
#[derive(Debug)]
struct Point {
    x: i32,
    y: i32,
}

fn main() {
    let origin = Point { x: 0, y: 0 };

    println!("Debug '?' {:?}", origin);
    println!("Debug '#?' {:#?}", origin);
}
```

Ou implementar de forma manual:

```rust
use std::fmt;

struct Point {
    x: i32,
    y: i32,
}

impl fmt::Debug for Point {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        f.debug_struct("Point")
            .field("x", &self.x)
            .field("y", &self.y)
            .finish()
    }
}

fn main() {
    let origin = Point { x: 0, y: 0 };

    println!("Debug '?' {:?}", origin);
    println!("Debug '#?' {:#?}", origin);
}
```
