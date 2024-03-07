+++
title = "Heap (Rust)"
author = ["Gabriel Rosa"]
date = 2024-03-05T23:07:00-03:00
tags = ["rust", "memory", "heap"]
draft = false
+++

tags
: [Ownership (Rust)]({{< relref "ownership_rust.md" >}})

source
: [What is Ownership? - The Rust Programming Language](https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html)

A heap possibilita receber e remover valores sem seguir uma ordem específica, como a stack.

Quando você coloca valores na heap, ela ira alocar um espaço vazio grande o suficiente para os novos dados, marcar esse espaço como "em uso" e retornar um pointeiro (o endereço de memória / onde está o conteúdo).

O ponteiro, por ter um tamanho fixo e conhecido, pode ser guardado na stack. E então, quando quiser obter os dados, é só seguir o ponteiro.


## Tipos guardados na heap {#tipos-guardados-na-heap}

-   `String`
-   `Box`


## Movendo dados {#movendo-dados}

As `String`, por exemplo, não implementam o trait `Copy`.

Quando tentamos copiar uma variável para a outra da mesma forma que fazemos com valores que implementam este trait, os valores são movidos:

```rust
fn main() {
    let s1 = String::from("hello");

    println!("s1 = {}\naddr = {:X}", s1, s1.as_ptr() as usize);

    let s2 = s1;

    println!("s2 = {}\naddr = {:X}", s2, s2.as_ptr() as usize);
}
```

Como o valor de `s1` foi movido para `s2`, se tentarmos chamar `s2` veremos que ele está indisponível.


## Cópia de dados {#cópia-de-dados}

Se quisermos copiar o valor de uma `String` para outra variável, basta utilizarmos o método `clone`:

```rust
fn main() {
    let s1 = String::from("hello");

    println!("s1 = {}\naddr = {:X}", s1, s1.as_ptr() as usize);

    let s2 = s1.clone();

    println!("s2 = {}\naddr = {:X}", s2, s2.as_ptr() as usize);
}
```

Já que o valor de `s1` foi copiado para `s2`, se tentarmos chamar a `s2` veremos que ela continua disponível.


## Funções e valores {#funções-e-valores}

Quando passamos valores para funções, esses valores são movidos para elas:

```rust
fn main() {
    let s = String::from("hello");

    println!("s = {}\naddress = {:X}", s, s.as_ptr() as usize);

    takes_ownership(s);
}

fn takes_ownership(some_string: String) {
    println!("some_string = {}\naddress = {:X}", some_string, some_string.as_ptr() as usize);
}
```


## Retorno de valores e escopo {#retorno-de-valores-e-escopo}

Quando retornamos valores de uma função, o ownership desses valores são transferidos:

```rust
fn main() {
    let s = gives_ownership();

    println!("s = {}\naddress = {:X}", s, s.as_ptr() as usize);
}

fn gives_ownership() -> String {
    let value = String::from("hello");

    println!("value = {}\naddress = {:X}", value, value.as_ptr() as usize);

    value
}
```

Quando passamos o valor como parâmetro de função, ele é movido para o parâmetro da função:

```rust
fn main() {
    let s = String::from("hello");

    println!("address = {:X}\ns = {}", s.as_ptr() as usize, s);

    println!("value = {}", move_and_return(s));
}

fn move_and_return(value: String) -> String {
    println!("address = {:X}", value.as_ptr() as usize);

    value
}
```
