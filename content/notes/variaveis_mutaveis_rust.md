+++
title = "Variáveis Mutáveis (Rust)"
author = ["Gabriel Rosa"]
date = 2023-11-11T23:56:00-03:00
tags = ["rust", "var", "mutability"]
draft = false
+++

tags
: [Variáveis (Rust)]({{< relref "associacao_de_variaveis_rust.md" >}})

source
: [Primitives - Rust By Example](https://doc.rust-lang.org/rust-by-example/primitives.html), [Mutability - Rust By Example](https://doc.rust-lang.org/rust-by-example/variable_bindings/mut.html)


## Declaração {#declaração}

As variáveis mutáveis são as variáveis que podem ter seus valores alterados. Porém, seu tipo não pode ser alterado.


### Demonstração {#demonstração}

Elas podem ser declaradas utilizando as palavras-chave `let` e `mut`:

```rust
let mut float1: f64 = 1.0;

println!("float1: {:?}", float1);

float1 = 2.0;

println!("float1: {:?}", float1);

let mut _unused_var = 456;

let other_var;
other_var = 789;
```


### Anatomia {#anatomia}

A síntaxe de declaração de variáveis imutáveis é essa:

`let mut <nome>:<tipo?> = <valor>`


#### Explicação {#explicação}

-   `let` =&gt; é a palavra-chave reservada para a declaração de variáveis
-   `mut` =&gt; é a palavra-chave reservada para especificar que a variável declarada é mutável
-   `<nome>` =&gt; é o nome da variável
-   `<tipo?>` (opcional) =&gt; é a anotação de tipo da variável
-   `<valor>` =&gt; é o valor da variável


#### Observações {#observações}

Se o `<tipo?>` não for usado na declaração da variável, você pode utilizar o tipo padrão da variável (para números inteiroes é `i32` e para números flutuantes é `f64`):

```rust
let mut an_integer = 365; // i32
let mut a_float = 45.0;   // f64
```

Ou então declarar o tipo no sufixo do valor da variável:

```rust
let mut another_integer = 365i32; // i32
let mut another_float = 444.4f64; // f64
```
