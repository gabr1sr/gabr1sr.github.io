+++
title = "Funções Const (Rust)"
author = ["Gabriel Rosa"]
date = 2024-02-28T15:40:00-03:00
draft = false
+++

tags
: [Funções (Rust)]({{< relref "funcoes_rust.md" >}})

source
: [Const functions (Functions) - The Rust Reference](https://doc.rust-lang.org/reference/items/functions.html#const-functions), [Const Functions (Constant Evaluation) - The Rust Reference](https://doc.rust-lang.org/reference/const_eval.html#const-functions), [Const generics - The Rust Reference](https://doc.rust-lang.org/reference/items/generics.html#const-generics), [Why can't the compiler detect that functions are constant without annotating them with const? - StackOverflow](https://stackoverflow.com/a/67941488)

Funções com o qualificador `const` são funções que podem ser chamadas dentro de contextos const.

Quando chamada dentro de um contexto const, a função é interpretada pelo compilador a tempo de compilação.

Declaração:

```rust
const fn add(x: i32, y: i32) -> i32 {
    x + y
}

const RESULT: i32 = add(1, 2);

println!("{}", RESULT);
```


## Características {#características}

-   Só aceita as ABIs `"Rust"` e `"C"` se usado o qualificador `extern`.
-   Não pode ser assíncrona.
-   Não pode ser usada para gerar números aleatórios (deve ser determinística).
-   Sempre irá retornar o mesmo resultado, independente de quantas vezes chamada.
-   Não pode fazer operações de ponto flutuante, só copiar/mover eles.
-   Pode usar const em generics e parâmetros lifetime.
