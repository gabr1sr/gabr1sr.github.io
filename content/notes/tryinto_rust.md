+++
title = "TryInto (Rust)"
author = ["Gabriel Rosa"]
date = 2024-01-15T01:10:00-03:00
draft = false
+++

tags
: [Conversão (Rust)]({{< relref "conversao_rust.md" >}})

source
: [TryFrom and TryInto - Rust By Example](https://doc.rust-lang.org/stable/rust-by-example/conversion/try_from_try_into.html)

É um `trait` genérico para converter entre tipos, similar ao [Into (Rust)]({{< relref "into_rust.md" >}}).

Porém, o `TryInto` é utilizado para conversões que possam falhar.

Sendo assim, ele retorna `Result`.

```rust
use std::convert::TryFrom;
use std::convert::TryInto;

#[derive(Debug, PartialEq)]
struct EvenNumber(i32);

impl TryFrom<i32> for EvenNumber {
    type Error = ();

    fn try_from(value: i32) -> Result<Self, Self::Error> {
        if value % 2 == 0 {
            Ok(EvenNumber(value))
        } else {
            Err(())
        }
    }
}

fn main() {
    let result: Result<EvenNumber, ()> = 8i32.try_into();
    assert_eq!(result, Ok(EvenNumber(8)));

    let result: Result<EvenNumber, ()> = 5i32.try_into();
    assert_eq!(result, Err(()));

    println!("Everything ok!");
}
```
