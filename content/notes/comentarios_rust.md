+++
title = "Comentários (Rust)"
author = ["Gabriel Rosa"]
date = 2023-11-12T00:18:00-03:00
tags = ["rust", "comments"]
draft = false
+++

tags
: [Rust]({{< relref "rust.md" >}})

source
: [Comments - Rust By Example](https://doc.rust-lang.org/rust-by-example/hello/comment.html), [Documentation - Rust By Example](https://doc.rust-lang.org/rust-by-example/meta/doc.html)


## Comentários padrões {#comentários-padrões}

São os comentários ignorados pelo compilador Rust.

Podem ser declarados da seguinte forma:

```rust
// Sou um comentário de uma linha

/* Sou um
 * /* /* comentário de */ */
 * várias
 * /* linhas */
 */
```


## Comentários de documentação {#comentários-de-documentação}

São os comentários que são processados por biblioteca HTML, utilizados para fins de documentar algo.

Eles suportam Markdown e podem ser declarados da seguinte forma:

```rust
#![crate_name = "doc"]

/// Essa estrutura representa um humano
pub struct Person {
    /// Uma pessoa deve ter um nome, não importa o quanto a Juliet possa odiar
    name: String,
}

impl Person {
    /// Retorna uma pessoa com o dado nome
    ///
    /// # Arguments
    ///
    /// * `name` - Uma string que contém o nome da pessoa
    ///
    /// # Examples
    ///
    /// ```
    /// // Você pode ter código Rust em blocos de código dentro de comentários
    /// // Se você passar --test no `rustdoc`, ele vai até mesmo testar para você!
    /// use doc::Person;
    /// let person = Person::new("name");
    /// ```
    pub fn new(name: &str) -> Person {
        Person {
            name: name.to_string(),
        }
    }

    /// Dá um olá amigo!
    ///
    /// Fala "Hello, [name](Person::name)" para a `Person` que é chamada.
    pub fn hello(&self) {
        println!("Hello, {}!", self.name);
    }
}

fn main() {
    let john = Person::new("John");

    john.hello();
}
```
