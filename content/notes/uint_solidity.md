+++
title = "Uint (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-26T04:41:00-03:00
draft = false
+++

tags
: [Tipos Básicos (Solidity)]({{< relref "tipos_basicos_solidity.md" >}})

source
: [Basic Solidity: Types](https://github.com/Cyfrin/foundry-full-course-f23#basic-solidity-types)

Em Solidity, os números inteiros sem sinais são declarados com a palavra-chave `uint` sozinha ou `uint` mais o número de bits na frente.

O número de bits podem ser: 8, 16, 24, 32, 40, 48, 56, 64, 72, 80, 88, 96, 104, 112, 120, 128, 136, 144, 152, 160, 168, 176, 184, 192, 200, 208, 216, 224, 232, 240, 248, 256.

O menor valor é 0 e o maior valor é `(2^bits) - 1`.

Comumente, trabalhamos com o `uint256`, que é o número inteiro sem sinais de 256 bits.

```solidity
// SPDX-License-Identifier: GPLv3
pragma solidity ^0.8.21;

contract UintExample {
    uint256 minValue = type(uint256).min; // 0
    uint256 maxValue = type(uint256).max; // 115792089237316195423570985008687907853269984665640564039457584007913129639935
    uint256 defaultValueZero; // 0

    function uint256Function() public pure returns (uint256) {
        return 1000;
    }
}
```
