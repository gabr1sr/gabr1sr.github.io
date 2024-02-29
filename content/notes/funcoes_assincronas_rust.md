+++
title = "Funções Assíncronas (Rust)"
author = ["Gabriel Rosa"]
date = 2024-02-28T15:57:00-03:00
draft = false
+++

tags
: [Funções (Rust)]({{< relref "funcoes_rust.md" >}})

source
: [Async functions - The Rust Reference](https://doc.rust-lang.org/reference/items/functions.html#async-functions)

Funções podem ser qualificadas como `async` e também pode ser combinado com o qualificador `unsafe`:

```rust
async fn regular_example() { }
async unsafe fn unsafe_example() { }
```

Funções assíncronas não funcionam quando chamadas.

Ao invés disso, elas capturam os argumentos em uma future.

Quando pesquisada (polled), essa future irá executar o corpo da função.

Uma função assíncrona é equivalente a uma função com um `async move` bloco como corpo e que retorna uma `impl Future`:

```rust
async fn example(x: &str) -> usize {
    x.len()
}
```

É o mesmo que:

```rust
fn example<'a>(x: &'a str) -> impl Future<Output = usize> + 'a {
    async move { x.len() }
}
```

Veja a source para mais informações.
