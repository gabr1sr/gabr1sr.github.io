+++
title = "Funções Genéricas (Rust)"
author = ["Gabriel Rosa"]
date = 2024-02-28T15:37:00-03:00
draft = false
+++

tags
: [Funções (Rust)]({{< relref "funcoes_rust.md" >}})

source
: [Generic functions - The Rust Reference](https://doc.rust-lang.org/reference/items/functions.html#generic-functions)


## Funções Genéricas {#funções-genéricas}

As funções do Rust também suportam o uso de generics.

Elas possibilitam que um ou mais tipos parametrizados apareçam na assinatura da função.

Cada parâmetro de tipo deve ser declarado explicitamente dentro de `<>` e separado por vírgula:

```rust
fn foo<A, B>(x: A, y: B) {
    // ...
}
```

Dentro da assinatura da função e do corpo dela, o nome do parâmetro de tipo pode ser usado como um tipo.

Os limites de Traits podem ser especificados para os parâmetros de tipo para permitir que os métodos com esse Trait sejam chamados nos valores desse tipo.

```rust
fn foo<T>(x: T) where T: Debug {
    // ...
}
```

Quando uma função genérica é referenciada, seu tipo é instanciado baseado no contexto da referência. Exemplo:

```rust
use std::fmt::Debug;

fn foo<T>(x: &[T]) where T: Debug {
    println!("{:?}", x);
}

foo(&[1, 2]);
```
