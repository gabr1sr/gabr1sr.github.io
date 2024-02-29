+++
title = "Funções (Rust)"
author = ["Gabriel Rosa"]
date = 2024-02-26T21:54:00-03:00
tags = ["rust", "function"]
draft = false
+++

tags
: [Rust]({{< relref "rust.md" >}})

source
: [functions - Comprehensive Rust](https://google.github.io/comprehensive-rust/control-flow-basics/functions.html), [Functions - The Rust Reference](https://doc.rust-lang.org/reference/items/functions.html)

A palavra-chave `fn` é utilizada para declarar funções.


## Anotação de Tipo {#anotação-de-tipo}

Podemos anotar tipos em funções utilizando `->`:

```rust
fn answer_to_life_the_universe_and_everything() -> i32 {
    42
}
```

Quando a anotação de tipo é omitida, o tipo retornado será unit type: `()`.


## Parâmetros {#parâmetros}

Podemos parametrizar as funções da seguinte forma:

```rust
fn add(x: i32, y: i32) -> i32 {
    x + y
}
```


## Corpo da Função {#corpo-da-função}

O corpo da função nada mais é do que o conteúdo da função.

Tudo o que estiver entre `{}` após a declaração da função faz parte do corpo dela:

```rust
fn foo() {
    // corpo da função
}
```


## Atributos em Funções {#atributos-em-funções}

Atributos externos são permitidos em funções.

```rust
#[test]
fn test_foo() {
    // ...
}
```

Atributos internos são permitidos dentro do corpo de funções.

```rust
fn documented() {
    #![doc = "Example"]
    // ...
}
```


## Atributos em Parâmetros de Funções {#atributos-em-parâmetros-de-funções}

Atributos externos são permitidos em parâmetros de funções.

Os atributos built-in permitidos são restringidos a apenas:

-   cfg
-   cfg_attr
-   allow
-   warn
-   deny
-   forbid

<!--listend-->

```rust
fn len(
    #[cfg(windows)] slice: &[u16],
    #[cfg(not(windows))] slice: &[u8],
) -> usize {
    slice.len()
}
```


## Outros {#outros}

-   [Funções Genéricas (Rust)]({{< relref "funcoes_genericas_rust.md" >}})
-   [Funções Assíncronas (Rust)]({{< relref "funcoes_assincronas_rust.md" >}})
-   [Funções Const (Rust)]({{< relref "funcoes_const_rust.md" >}})
-   [Extern (Rust)]({{< relref "extern_rust.md" >}})
