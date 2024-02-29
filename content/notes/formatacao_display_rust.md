+++
title = "Formatação Display (Rust)"
author = ["Gabriel Rosa"]
date = 2023-11-13T07:37:00-03:00
tags = ["rust", "macro", "format", "display"]
draft = false
+++

tags
: [Formatação (Rust)]({{< relref "formatacao_rust.md" >}})

source
: [Formatted print - Rust By Example](https://doc.rust-lang.org/rust-by-example/hello/print.html), [Display - Rust By Example](https://doc.rust-lang.org/rust-by-example/hello/print/print_display.html), [std::fmt Module](https://doc.rust-lang.org/std/fmt/), [std::fmt::Display Trait](https://doc.rust-lang.org/std/fmt/trait.Display.html)

É o `trait` da `std::fmt` utilizado para visualização.

Todos os tipos que quiserem ser impressos usando ele devem ter uma implementação para `fmt::Display`.

Não há como utilizar `derive` para criar uma implementação automaticamente.

Os tipos da `std` já têm essa implementação, com exceção do `struct`.


## Flags {#flags}

-   _vazio_ =&gt; Visualização padrão (`fmt::Display`)
-   `o` =&gt; Visualização com inteiros octais (`fmt::Octal`)
-   `x` =&gt; Visualização com inteiros hexadecimais em minúsculo (`fmt::LowerHex`)
-   `X` =&gt; Visualização com inteiros hexadecimais em maiúsculo (`fmt::UpperHex`)
-   `p` =&gt; Visualização de endereço de memória de ponteiro (`fmt::Pointer`)
-   `b` =&gt; Visualização com inteiros binários (`fmt::Binary`)
-   `e` =&gt; Visualização com inteiros em notação científica em minúsculo (`fmt::LowerExp`)
-   `E` =&gt; Visualização com inteiros em notação científica em maiúsculo (`fmt::UpperExp`)


## Como Usar {#como-usar}

Para os tipos que já têm essa implementação, você pode usar da seguinte forma:

```rust
fn main() {
    let value: i32 = 45;

    println!("Display '' {}", value);
    println!("Display 'o' {:o}", value);
    println!("Display 'x' {:x}", value);
    println!("Display 'X' {:X}", value);
    println!("Display 'p' {:p}", &value);
    println!("Display 'b' {:b}", value);
    println!("Display 'e' {:e}", value);
    println!("Display 'E' {:E}", value);
}
```

Para os tipos que não têm essa implementação, como o `struct`, por exemplo, devemos implementar manualmente:

```rust
use std::fmt;

struct Point {
    x: i32,
    y: i32,
}

impl fmt::Display for Point {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        write!(f, "({}, {})", self.x, self.y)
    }
}

fn main() {
    let origin = Point { x: 0, y: 0 };

    println!("Display '' {}", origin);
}
```
