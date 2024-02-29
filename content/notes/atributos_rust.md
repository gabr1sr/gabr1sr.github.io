+++
title = "Atributos (Rust)"
author = ["Gabriel Rosa"]
date = 2024-02-28T16:24:00-03:00
draft = false
+++

tags
: [Rust]({{< relref "rust.md" >}})

source
: [Atributtes - The Rust Reference](https://doc.rust-lang.org/reference/attributes.html)

Os atributos são uma forma livre e geral de metadados que é interpretada de acordo com o nome, convenção, linguagem e versão do compilador.

São modelados baseados nos atributos do [ECMA-335](https://ecma-international.org/publications-and-standards/standards/ecma-335/) com a síntaxe baseada no C# ([ECMA-334](https://ecma-international.org/publications-and-standards/standards/ecma-334/)).


## Atributos Externos {#atributos-externos}

São os atributos escritos com apenas `#`.

```rust
#[attribute_here]
fn foo() { /* ... */ }
```


## Atributos Internos {#atributos-internos}

São os atributos escritos com `#` seguido de `!`.

```rust
fn foo() {
    #![attribute_here]
    // ...
}
```
