+++
title = "Extern (Rust)"
author = ["Gabriel Rosa"]
date = 2024-02-28T15:38:00-03:00
draft = false
+++

tags
: [Funções (Rust)]({{< relref "funcoes_rust.md" >}})

source
: [External blocks - The Rust Reference](https://doc.rust-lang.org/reference/items/external-blocks.html), [Variadic functions - The Rust Reference](https://doc.rust-lang.org/reference/items/external-blocks.html#variadic-functions), [Extern function qualifier - The Rust Reference](https://doc.rust-lang.org/reference/items/functions.html#extern-function-qualifier)
    -   Extern

O qualificador de função `extern` possibilita providenciar definições de função que podem ser chamadas com uma ABI particular:

```rust
extern "ABI" fn foo() { /* ... */ }
```

Elas geralmente são usadas em conjunto com um blocos externos, que podem providenciar declaração de funções que podem ser usadas para chamar funções sem providenciar sua definição:

```rust
extern "ABI" {
    fn foo(); /* sem corpo */
}

unsafe { foo() }
```

Quando o qualificador `extern` é omitido, a ABI `"Rust"` é usada por padrão. Exemplo:

```rust
fn foo() {}
```

É o mesmo que:

```rust
extern "Rust" fn foo() {}
```

Funções podem ser chamadas por códigos externos e usar uma ABI que difere do Rust permite, por exemplo, providenciar funções que podem ser chamadas de outras linguagens como C:

```rust
// Declara uma função com a ABI "C"
extern "C" fn new_i32() -> i32 { 0 }

// Declara uma função com a ABI "stdcall"
extern "stdcall" fn new_i32_stdcall() -> i32 { 0 }
```

Assim como os blocos externos, quando o `extern` é usado, mas a `"ABI"` é omitida, a ABI padrão utilizada é `"C"`.

```rust
extern fn new_i32() -> i32 { 0 }
let fptr: extern fn() -> i32 = new_i32;
```

É equivalente a:

```rust
extern "C" fn new_i32() -> i32 { 0 }
let fptr: extern "C" fn() -> i32 = new_i32;
```


## Funções Variádicas {#funções-variádicas}

Funções dentro de blocos externos podem ser variádicas especificando `...` como último argumento.

Para isso funcionar, deve haver pelo menos um parâmetro antes do parâmetro variádico.

Ele pode ser opcionalmente especificado com um identificador:

```rust
extern "C" {
    fn foo(x: i32, ...); // sem identificador
    fn with_name(format: *const u8, args: ...); // com identificador
}
```


## ABIs Suportadas {#abis-suportadas}

-   Rust
-   C
-   system
-   cdecl
-   stdcall
-   win64
-   sysv64
-   aapcs
-   fastcall
-   vectorcall
-   thiscall
-   eficall
