+++
title = "Address (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-12-07T22:00:00-03:00
draft = false
+++

tags
: [Tipos Básicos (Solidity)]({{< relref "tipos_basicos_solidity.md" >}})

source
: [Updraft Cyfrin | Basic variable types](https://updraft.cyfrin.io/courses/solidity/simple-storage/solidity-basic-types?lesson_format=video)

Em Solidity, os endereços de carteiras e contratos são declarados com a palavra-chave `address`.

Um `address` ocupa 20 bytes de espaço (160 bits).

Eles recebem um valor em hexadecimal com o sufixo `0x`.

```solidity
// SPDX-License-Identifier: GPLv3
pragma solidity ^0.8.0;

contract AddressExample {
    address minValue = address(type(uint160).min); // 0x0000000000000000000000000000000000000000
    address maxValue = address(type(uint160).max); // 0xFFfFfFffFFfffFFfFFfFFFFFffFFFffffFfFFFfF
    address defaultValueZero; // 0x0000000000000000000000000000000000000000

    function addressFunction() public pure returns (address) {
        return 0x00000000000000000000000000000000DeaDBeef;
    }
}
```
