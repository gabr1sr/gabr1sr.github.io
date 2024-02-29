+++
title = "Convertendo Strings (Rust)"
author = ["Gabriel Rosa"]
date = 2024-01-15T01:16:00-03:00
tags = ["rust", "string", "conversion"]
draft = false
+++

tags
: [Strings (Rust)]({{< relref "strings_rust.md" >}}), [Conversão (Rust)]({{< relref "conversao_rust.md" >}})

source
: [To and from Strings - Rust By Example](https://doc.rust-lang.org/stable/rust-by-example/conversion/string.html)


## Convertendo para String {#convertendo-para-string}

Podemos converter qualquer tipo para `String` implementando o `trait` `ToString` para o tipo.

Ao invés de fazer isso diretamente, você pode implementar o `trait` `fmt::Display` que já providencia o `ToString` e também possibilita você usá-lo ao printar.

```rust
use std::fmt;

struct Circle {
    radius: i32
}

impl fmt::Display for Circle {
    fn fmt(&self, f: &mut fmt::Formatter) -> fmt::Result {
        write!(f, "Circle of radius {}", self.radius)
    }
}

fn main() {
    let circle = Circle { radius: 6 };
    println!("{}", circle.to_string());
}
```


## Convertendo de uma String {#convertendo-de-uma-string}

Podemos converter uma `String` para outro tipo utilizando a função `parse`, especificando o tipo ou inferindo o tipo.

Isso só irá funcionar se o tipo destinado implementa o `trait` `FromStr`.

```rust
fn main() {
    let parsed: i32 = "5".parse().unwrap();
    let turbo_parsed = "10".parse::<i32>().unwrap();

    let sum = parsed + turbo_parsed;
    println!("Sum: {:?}", sum);
}
```
