+++
title = "Casting (Rust)"
author = ["Gabriel Rosa"]
date = 2023-11-17T07:00:00-03:00
tags = ["rust", "type", "cast"]
draft = false
+++

tags
: [Tipagem (Rust)]({{< relref "tipagem_rust.md" >}})

source
: [Casting - Rust By Example](https://doc.rust-lang.org/rust-by-example/types/cast.html)

Casting é a técnica de conveter tipos explicitamente.

Na linguagem Rust, ela é feita através da palavra-chave `as`.

```rust
let decimal = 65.4321f32;

// Conversão explícita
let integer = decimal as u8;
let character = integer as char;

println!("Casting: {} -> {} -> {}", decimal, integer, character);
```

Quando convertemos um valor para um tipo sem sinais, `T`, a conta realizada para calcular o novo valor é:

-   Quando o `valor` é positivo: `valor % (T::MAX + 1)`.
-   Quando o `valor` é negativo: `(T::MAX + valor - 1) % (T::MAX + 1)`.

Debaixo dos panos, os primeiros 8 bits menos significantes (LSB) são mantidos, enquanto o resto dos bits mais significativos (MSB) são truncados.

```rust
#![allow(overflowing_literals)]

// Ao menos que o valor caiba no tipo
println!("1000 as u16: {}", 1000 as u16);

// 1000 % 256 = 232
println!("1000 as u8: {}", 1000 as u8);

// -1 = (256 - 1) % 256 = 255
println!("-1 as u8: {}", (-1i8) as u8);

// 1000 % 256 = 232
println!("1000 mod 256: {}", 1000 % 256);
```

Quando convertemos um valor para um tipo com sinais, o resultado é o mesmo que quando sem sinais. Porém, se o bit mais significante desse valor é 1, o valor será negativo.

```rust
#![allow(overflowing_literals)]

println!("128 as i16: {}", 128 as i16);

println!("128 as i8: {}", 128 as i8);

println!("1000 as u8: {}", 1000 as u8);

println!("232 as i8: {}", 232 as i8);
```

Desde o Rust 1.45, a palavra-chave `as` faz um **saturating cast** quando convertendo de um `float` para um `int`.

Se o valor do ponto flutuante exceder o limite superior ou for menor que o limite inferior, o valor retornado será igual ao limite cruzado.

```rust
println!("300.0 as u8: {}", 300.0f32 as u8);

println!("-100.0 as u8: {}", -100.0f32 as u8);

println!("nan as u8: {}", f32::NAN as u8);
```

Esse comportamento tem um pequeno custo em runtime que pode ser evitado com métodos `unsafe`.

No entanto, os resultados podem transbordar e retornar valores inconsistentes.

Use com sabedoria.

```rust
unsafe {
    println!("300.0 as u8: {}", 300.0f32.to_int_unchecked::<u8>());

    println!("-100.0 as u8: {}", (-100.0f32).to_int_unchecked::<u8>());

    println!("nan as u8: {}", f32::NAN.to_int_unchecked::<u8>());
}
```
