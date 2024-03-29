+++
title = "Strings (Rust)"
author = ["Gabriel Rosa"]
date = 2023-11-15T18:11:00-03:00
tags = ["rust", "type", "primitive", "string"]
draft = false
+++

tags
: [Tipos Primitivos (Rust)]({{< relref "tipos_primitivos_rust.md" >}})

source
: [Primitives - Rust By Example](https://doc.rust-lang.org/rust-by-example/primitives.html), [Primitive Types - std Crate](https://doc.rust-lang.org/std/#primitives), [Strings - Rust By Example](https://doc.rust-lang.org/rust-by-example/std/str.html)

Na linguagem Rust, as strings podem ser divididas em 2 tipos:

-   `String` =&gt; um vetor de bytes (`Vec<u8>`) que garante sempre ser uma sequência UTF-8 válida.
-   `&str` =&gt; um slice (`&[u8]`) que sempre aponta para uma sequência UTF-8 válida e que pode ser usada para ver em uma `String`, assim como `&[T]` consegue ver em `Vec<T>`. (Veja [Slices]({{< relref "slices_rust.md" >}}))

O `&str` é um acrônimo para `&'static str`. `static` é um lifetime.


## Declaração {#declaração}

Podemos declarar strings das seguintes formas:


### Literal (slice de String) {#literal--slice-de-string}

Uma string literal é uma string imutável e de tamanho conhecido.

Ela é alocada na stack.

E pode ser declarada das seguintes formas:

```rust
let string1: &'static str = "Hello";
let string2: &str = "World";
let string3 = "Hello, World!";

fn type_of<T>(_: &T) -> &'static str {
    std::any::type_name::<T>()
}

println!("string1: {} = {:?}", type_of(&string1), string1);
println!("string2: {} = {:?}", type_of(&string2), string2);
println!("string3: {} = {:?}", type_of(&string3), string3);
```


### String a partir de um slice de String {#string-a-partir-de-um-slice-de-string}

A string é alocada na Heap e um ponteiro para seu endereço é alocado na Stack.

Se a variável for imutável, cada alteração deverá ser salva em outra variável (alocando mais memória).

```rust
let alice = String::from("Alice");
let bob: String = alice.replace("Alice", "Bob");

fn type_of<T>(_: &T) -> &'static str {
    std::any::type_name::<T>()
}

println!("alice: {} = {:?}", type_of(&alice), alice);
println!("bob: {} = {:?}", type_of(&bob), bob);
```

Uma `String` é feita de 3 partes:

-   ponteiro (ou ptr) =&gt; aponta para o endereço de memória em que o conteúdo da `String` está
-   tamanho (ou length) =&gt; quantos bytes o conteúdo da `String` está usando
-   capacidade (ou capacity) =&gt; quantidade total de memória, em bytes, que a `String` recebeu do alocador

Essas partes são guardadas na stack, equanto o conteúdo da string é guardado na heap.

```rust
let s1 = String::from("hello");
```

{{< figure src="/ox-hugo/2024-03-06_23-45-55_screenshot.png" >}}


## Códigos {#códigos}

<a id="code-snippet--type-of"></a>
```rust
fn type_of<T>(_: &T) -> &'static str {
    std::any::type_name::<T>()
}
```

<a id="code-snippet--show-literal-str-results"></a>
```rust
fn type_of<T>(_: &T) -> &'static str {
    std::any::type_name::<T>()
}

println!("string1: {} = {:?}", type_of(&string1), string1);
println!("string2: {} = {:?}", type_of(&string2), string2);
println!("string3: {} = {:?}", type_of(&string3), string3);
```

<a id="code-snippet--show-string-from-slice-results"></a>
```rust
fn type_of<T>(_: &T) -> &'static str {
    std::any::type_name::<T>()
}

println!("alice: {} = {:?}", type_of(&alice), alice);
println!("bob: {} = {:?}", type_of(&bob), bob);
```
