+++
title = "Int (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-12-06T16:14:00-03:00
draft = false
+++

tags
: [Tipos Básicos (Solidity)]({{< relref "tipos_basicos_solidity.md" >}})

source
: [Updraft Cyfrin | Basic variable types](https://updraft.cyfrin.io/courses/solidity/simple-storage/solidity-basic-types?lesson_format=video)

Em Solidity, os números inteiros com sinais são declarados com a palavra-chave `int` sozinha ou `int` mais o número de bits na frente.

O número de bits podem ser: 8, 16, 24, 32, 40, 48, 56, 64, 72, 80, 88, 96, 104, 112, 120, 128, 136, 144, 152, 160, 168, 176, 184, 192, 200, 208, 216, 224, 232, 240, 248, 256.

O menor valor é 0 e o maior valor é `(2^(bits - 1)) - 1`.

Raramente trabalhamos com o `int256` , que é o número inteiro, com sinais, de 256 bits.

```solidity
// SPDX-License-Identifier: GPLv3
pragma solidity ^0.8.21;

contract IntExample {
    int256 minValue = type(int256).min; // -57896044618658097711785492504343953926634992332820282019728792003956564819968
    int256 maxValue = type(int256).max; // 57896044618658097711785492504343953926634992332820282019728792003956564819967
    int256 defaultValueZero; // 0

    function int256Function() public pure returns (int256) {
        return 123;
    }
}
```
