+++
title = "TryFrom (Rust)"
author = ["Gabriel Rosa"]
date = 2024-01-15T01:05:00-03:00
draft = false
+++

tags
: [Conversão (Rust)]({{< relref "conversao_rust.md" >}})

source
: [TryFrom and TryInto - Rust By Example](https://doc.rust-lang.org/stable/rust-by-example/conversion/try_from_try_into.html)

É um `trait` genérico para converter entre tipos, similar ao [From (Rust)]({{< relref "from_rust.md" >}}).

Porém, o `TryFrom` é utilizado para conversões que possam falhar.

Sendo assim, ele retorna `Result`.

```rust
use std::convert::TryFrom;

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
    assert_eq!(EvenNumber::try_from(8), Ok(EvenNumber(8)));
    assert_eq!(EvenNumber::try_from(5), Err(()));
    println!("Everything ok!");
}
```
