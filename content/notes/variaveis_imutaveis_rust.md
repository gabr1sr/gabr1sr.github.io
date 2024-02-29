+++
title = "Variáveis Imutáveis (Rust)"
author = ["Gabriel Rosa"]
date = 2023-11-11T23:46:00-03:00
tags = ["rust", "var", "immutability"]
draft = false
+++

tags
: [Variáveis (Rust)]({{< relref "associacao_de_variaveis_rust.md" >}})

source
: [Primitives - Rust by Example](https://doc.rust-lang.org/rust-by-example/primitives.html)


## Declaração {#declaração}

As variáveis imutáveis são as variáveis padrões declaradas na linguagem Rust.


### Demonstração {#demonstração}

Elas podem ser declaradas utilizando a palavra-chave `let`:

```rust
let float1: f64 = 1.0;
let float2 = 2.0f64;
let float3 = 3.0;
let _unused_var = 123;
let other_var;
other_var = 456;
```


### Anatomia {#anatomia}

A síntaxe de declaração de variáveis imutáveis é essa:

`let <nome>:<tipo?> = <valor>`


#### Explicação {#explicação}

-   `let` =&gt; é a palavra-chave reservada para a declaração de variáveis
-   `<nome>` =&gt; é o nome da variável
-   `<tipo?>` (opcional) =&gt; é a anotação de tipo da variável
-   `<valor>` =&gt; é o valor da variável


#### Observações {#observações}

Se o `<tipo?>` não for usado na declaração da variável, você pode utilizar o tipo padrão da variável (para números inteiroes é `i32` e para números flutuantes é `f64`):

```rust
let an_integer = 365; // i32
let a_float = 45.0;   // f64
```

Ou então declarar o tipo no sufixo do valor da variável:

```rust
let another_integer = 365i32; // i32
let another_float = 444.4f64; // f64
```
