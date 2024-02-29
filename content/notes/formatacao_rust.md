+++
title = "Formatação (Rust)"
author = ["Gabriel Rosa"]
date = 2023-11-12T07:58:00-03:00
tags = ["rust", "macro", "format"]
draft = false
+++

tags
: [Rust]({{< relref "rust.md" >}})

source
: [Formatted print - Rust By Example](https://doc.rust-lang.org/rust-by-example/hello/print.html), [std::fmt Module](https://doc.rust-lang.org/std/fmt/)

No Rust, podemos utilizar a macro `format!` para usar interpolação de expressões em tempo de execução.


## Flags e Traits de Formatação {#flags-e-traits-de-formatação}

-   _vazio_ =&gt; `std::fmt::Display`
-   `?` =&gt; `std::fmt::Debug` (precisa usar o atributo `derive` para `struct`)
-   `x?` =&gt; `std::fmt::Debug` com hexadecimais em minúsculo
-   `X?` =&gt; `std::fmt::Debug` com hexadecimais em maiúsculo
-   `o` =&gt; `std::fmt::Octal`
-   `x` =&gt; `std::fmt::LowerHex`
-   `X` =&gt; `std::fmt::UpperHex`
-   `p` =&gt; `std::fmt::Pointer`
-   `b` =&gt; `std::fmt::Binary`
-   `e` =&gt; `std::fmt::LowerExp`
-   `E` =&gt; `std::fmt::UpperExp`


## Tipos de Formatação {#tipos-de-formatação}

-   [Formatação Debug (Rust)]({{< relref "formatacao_debug_rust.md" >}})
-   [Formatação Display (Rust)]({{< relref "formatacao_display_rust.md" >}})


## Utilizado Por {#utilizado-por}

-   [Printing (Rust)]({{< relref "printing_rust.md" >}})
