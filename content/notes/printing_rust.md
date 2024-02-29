+++
title = "Printing (Rust)"
author = ["Gabriel Rosa"]
date = 2023-11-13T06:20:00-03:00
tags = ["rust", "macro", "print"]
draft = false
+++

tags
: [Rust]({{< relref "rust.md" >}})

source
: [Formatted print - Rust By Example](https://doc.rust-lang.org/rust-by-example/hello/print.html), [std::fmt Module](https://doc.rust-lang.org/std/fmt/), [std::print Macro](https://doc.rust-lang.org/std/macro.print.html), [std::println Macro](https://doc.rust-lang.org/std/macro.println.html), [std::eprint Macro](https://doc.rust-lang.org/std/macro.eprint.html), [std::eprintln Macro](https://doc.rust-lang.org/std/macro.eprintln.html)

A impressão (printing) na linguagem Rust é realizada através de uma série de `macros` definidas na `std::fmt`.


## Macros de Impressão {#macros-de-impressão}

-   `format!` =&gt; escreve texto formatado para `String` (veja [Formatação]({{< relref "formatacao_rust.md" >}})).
-   `print!` =&gt; o mesmo que `format!`, mas o texto é impresso no console (`io::stdout`).
-   `println!` =&gt; o mesmo que o `print!`, mas uma nova linha é adicionada.
-   `eprint!` =&gt; o mesmo que o `print!`, mas o texto é impresso na saída de erro padrão (`io::stderr`).
-   `eprintln!` =&gt; o mesmo que o `eprint!`, mas uma nova linha é adicionada.


### print! {#print}

Escreverá o texto na saída padrão, mas dará pânico caso escrever na `io::stdout()` falhe.

```rust
print!("Hello, World!");
print!("Hello again!");
```

Essa macro vai bloquear a saída padrão a cada chamada. Se você chamar `print!` dentro de um loop, esse comportamento pode gerar atrasos.

Para evitar este problema, bloqueie a stdout usando `io::stdout().lock()`:

```rust
use std::io::{stdout, Write};

let mut lock = stdout().lock();
write!(lock, "Hello, World!").unwrap();
```


### println! {#println}

Escreverá o texto na saída padrão, mas dará pânico caso escrever na `io::stdout()` falhe.

```rust
println!("Hello, World!");
println!("Hello again!");
```

Essa macro vai bloquear a saída padrão a cada chamada. Se você chamar `println!` dentro de um loop, esse comportamento pode gerar atrasos.

Para evitar este problema, bloqueie a stdout usando `io::stdout().lock()`:

```rust
use std::io::{stdout, Write};

let mut lock = stdout().lock();
writeln!(lock, "Hello, World!").unwrap();
```


### eprint! {#eprint}

Mesmo caso que o `print!`, porém, utilizará a `io::stderr` ao invés da `io::stdout`.

```rust
eprint!("Hello, World!");
```

Utilize apenas para mensagens de erro e progresso.


### eprintln! {#eprintln}

Mesma coisa que o `println!`, porém, utilizará a `io::stderr` ao invés da `io::stdout`.

Utilize apenas para mensagens de erro e progresso.


## Utilidades {#utilidades}

-   Para limpar a stdout, você pode usar `io::stdout().flush().unwrap()`
-   Para limpar a stderr, você pode usar `io::stderr().flush().unwrap()`
