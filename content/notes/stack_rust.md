+++
title = "Stack (Rust)"
author = ["Gabriel Rosa"]
date = 2024-03-05T23:08:00-03:00
tags = ["rust", "memory", "stack"]
draft = false
+++

tags
: [Ownership (Rust)]({{< relref "ownership_rust.md" >}})

source
: [What is Ownership? - The Rust Programming Language](https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html)

A stack, ou pilha, guarda valores na ordem em que ela recebe (FIFO) e os remove na ordem oposta (LIFO).

Toda informação guardada dentro da stack deve haver um tamanho fixo conhecido.

Dados com tamanhos desconhecidos no tempo de compilação ou que podem mudar devem ser guardados na heap.

Ela é mais rápida do que a heap, por conta do local em que os dados novos serão inseridos estarem fáceis de achar (no topo).

Quando seu código chama uma função, os valores passados na função e as variáveis locais da função são colocadas na stack. Quando a função acaba, esses valores são removidos da stack.


## Tipos guardados na stack {#tipos-guardados-na-stack}

Os seguintes tipos de dados são guardados por padrão na stack:

-   Números inteiros
-   Booleanos
-   Números de ponto-flutuante
-   Caractere único
-   Tuplas (se contém apenas tipos que implementam o trait `Copy`)


## Cópia de dados {#cópia-de-dados}

Para os tipos de dados que são guardados na stack, podemos copiá-los de uma variável para outra da seguinte forma, sem usar `clone`:

```rust
let x = 5;
let y = x;

println!("x = {}, y = {}", x, y);
```

Isso ocorre pelos seguintes motivos:

1.  valores que são guardados na stack são previsíveis e têm tamanho fixo
2.  tipos que são guardados na stack utilizam o trait `Copy` que automaticamente copia o valor quando atribuído a outra variável

Quando o programa sair do escopo e a função `drop` for chamada, tanto a variável `x` quanto a `y` serão liberadas.


## Funções e valores {#funções-e-valores}

Quando passamos valores para funções, esses valores, ao invés de serem movidos para a função, são copiados para ela, possibilitando utilizá-los mesmo depois da chamada de função:

```rust
fn main() {
    let x: i32 = 5;
    let x_addr = std::ptr::addr_of!(x);
    println!("outside function: {}\naddr: {:X}", x, x_addr as usize);

    makes_copy(x);
}

fn makes_copy(some_integer: i32) {
    let some_integer_addr = std::ptr::addr_of!(some_integer);
    println!("inside function: {}\naddr: {:X}", some_integer, some_integer_addr as usize);
}
```


## Retorno de valores e escopo {#retorno-de-valores-e-escopo}

Quando retornamos valores de uma função, o ownership desses valores são transferidos:

```rust
fn main() {
    let x1 = gives_ownership();
    println!("x1 = {}", x1);

    let x1_addr = std::ptr::addr_of!(x1);
    println!("'x1' address = {:X}", x1_addr as usize);
}

fn gives_ownership() -> i32 {
    let value = 42;
    println!("value = {}", value);

    let value_addr = std::ptr::addr_of!(value);
    println!("'value' address = {:X}", value_addr as usize);

    value
}
```

Quando passamos o valor como parâmetro de função, ele é copiado para o parâmetro da função:

```rust
fn main() {
    let x1: i32 = 5;
    let x1_addr = std::ptr::addr_of!(x1);
    println!("addr = {:X}\nx1 = {}", x1_addr as usize, x1);
    println!("value = {}", copy_and_return(x1));
}

fn copy_and_return(value: i32) -> i32 {
    let addr = std::ptr::addr_of!(value);
    println!("addr = {:X}", addr as usize);

    value
}
```
