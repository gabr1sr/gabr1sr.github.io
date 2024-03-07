+++
title = "Referências (Rust)"
author = ["Gabriel Rosa"]
date = 2024-03-07T12:02:00-03:00
tags = ["rust", "memory", "reference"]
draft = false
+++

tags
: [Ownership (Rust)]({{< relref "ownership_rust.md" >}})

source
: [References and Borrowing - The Rust Programming Language](https://doc.rust-lang.org/book/ch04-02-references-and-borrowing.html)

As referências, no Rust, funcionam como ponteiros: elas apontam para um endereço que contém informações guardadas de alguma outra variável.

Diferente dos ponteiros, as referências apontam para um valor válido de um tipo particular enquanto esta referência existir.

Podemos declarar uma referência utilizando `&`:

```rust
fn main() {
    let s1 = String::from("hello");

    let len = calculate_length(&s1);

    println!("The length of '{}' is {}.", s1, len);
}

fn calculate_length(s: &String) -> usize {
    s.len()
}
```

{{< figure src="/ox-hugo/2024-03-07_12-10-28_screenshot.png" >}}


## Referências mutáveis {#referências-mutáveis}

Quando queremos alterar o valor de uma variável/valor referenciado, podemos utilizar `&mut`:

```rust
fn main() {
    let mut s = String::from("hello");

    println!("Before: {}", s);

    change(&mut s);

    println!("After: {}", s);
}

fn change(some_string: &mut String) {
    some_string.push_str(", world");
}
```


## Limites {#limites}

Só podemos ter uma referência mutável por valor.

Não podemos ter uma referência mutável após outras referências imutáveis do mesmo valor antes que elas sejam utilizadas:

```rust
let mut s = String::from("hello");

let r1 = &s;
let r2 = &s;
let r3 = &mut s;

println!("{}, {} and {}", r1, r2, r3);
```

Apenas depois que nós já utilizamos as referências imutáveis:

```rust
let mut s = String::from("hello");

let r1 = &s;
let r2 = &s;

println!("{} and {}", r1, r2);

let r3 = &mut s;

println!("{}", r3);
```
