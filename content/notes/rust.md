+++
title = "Rust"
author = ["Gabriel Rosa"]
date = 2023-11-11T04:11:00-03:00
tags = ["rust", "lang", "programming"]
draft = false
+++

tags
: [Linguagem de Programação]({{< relref "linguagem_de_programacao.md" >}})

source
: [Foreword - The Rust Programming Language (Book)](https://doc.rust-lang.org/book/foreword.html), [O Ecossistema Rust](https://google.github.io/comprehensive-rust/pt-BR/cargo/rust-ecosystem.html), [O que é Rust?](https://google.github.io/comprehensive-rust/pt-BR/hello-world/what-is-rust.html), [Benefícios do Rust](https://google.github.io/comprehensive-rust/pt-BR/hello-world/benefits.html), [Olá, Mundo](https://google.github.io/comprehensive-rust/pt-BR/types-and-values/hello-world.html)


## Sobre {#sobre}

Rust é uma linguagem de programação designada para ser eficiente em termos de velocidade e utilização de memória.

Ela é compilada estaticamente e tem um papel semelhante ao C++.


### Paradigmas {#paradigmas}

-   Imperativo
-   Declarativo
-   Funcionalidades de programação orientada à objetos (POO)
-   Conceitos de programação funcional


### Plataformas suportadas {#plataformas-suportadas}

-   Linux
-   Windows
-   Mac OS


### Arquiteturas suportadas {#arquiteturas-suportadas}

-   x86
-   x86_64
-   ARM
-   WebAssembly


### Dispositivos suportados {#dispositivos-suportados}

-   Firmware
-   Bootloaders
-   Smart displays
-   Celulares
-   Desktops
-   Servidores


## Benefícios {#benefícios}

Alguns benefícios que a linguagem oferece:


### Segurança em memória em tempo de compilação {#segurança-em-memória-em-tempo-de-compilação}

-   Sem variáveis não inicializadas.
-   Sem double-frees.
-   Sem use-after-free.
-   Sem ponteiros `NULL`.
-   Sem mutexes bloqueados esquecidos.
-   Sem concorrência de dados entre threads.
-   Sem invalidação de iteradores.


### Sem comportamento indefinido em tempo de execução {#sem-comportamento-indefinido-em-tempo-de-execução}

-   O acesso a matrizes tem limites verificados.
-   Estouro de números inteiros é definido ("pânico" ou wrap-around).


### Recursos de linguagem modernos {#recursos-de-linguagem-modernos}

-   Enums e pattern matching.
-   Generics.
-   FFI sem overhead.
-   Abstrações de custo zero.
-   Excelentes mensagens de erro do compilador.
-   Gerenciador de dependências integrado.
-   Suporte integrado para testes.
-   Excelente suporte ao LSP.


## Ecossistema {#ecossistema}

O ecossistema Rust consiste em várias ferramentas:


### Rustc {#rustc}

-   Converte arquivos `.rs` em binários ou formatos intermediários.
-   Usa a LLVM como backend.


### Cargo {#cargo}

-   Gerencia dependências de projetos.
-   Ferramenta de compilação do Rust.


### Rustup {#rustup}

-   Instala e atualiza o conjunto de ferramentas do Rust.


## Conteúdos {#conteúdos}

-   [Lista de Conteúdos (Rust)]({{< relref "lista_de_conteudos_rust.md" >}})


## Básico {#básico}

-   [Comentários (Rust)]({{< relref "comentarios_rust.md" >}})
-   [Associação de Variáveis (Rust)]({{< relref "associacao_de_variaveis_rust.md" >}})
-   [Tipagem (Rust)]({{< relref "tipagem_rust.md" >}})
-   [Escopo (Rust)]({{< relref "escopo_rust.md" >}})
-   [Conversão (Rust)]({{< relref "conversao_rust.md" >}})
-   [Expressões (Rust)]({{< relref "expressoes_rust.md" >}})
-   [Controle de Fluxo (Rust)]({{< relref "controle_de_fluxo_rust.md" >}})
-   [Funções (Rust)]({{< relref "funcoes_rust.md" >}})
-   [Atributos (Rust)]({{< relref "atributos_rust.md" >}})


## Avançado {#avançado}

-   [Macros (Rust)]({{< relref "macros_rust.md" >}})


## Conceitos {#conceitos}

-   [Printing (Rust)]({{< relref "printing_rust.md" >}})
-   [Formatação (Rust)]({{< relref "formatacao_rust.md" >}})
