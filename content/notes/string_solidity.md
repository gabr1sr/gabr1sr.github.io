+++
title = "String (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-12-07T23:13:00-03:00
draft = false
+++

tags
: [Tipos Básicos (Solidity)]({{< relref "tipos_basicos_solidity.md" >}})

source
: [Updraft Cyfrin | Basic variable types](https://updraft.cyfrin.io/courses/solidity/simple-storage/solidity-basic-types?lesson_format=video), [Solidity Docs | Dynamically-sized byte array](https://docs.soliditylang.org/en/latest/types.html#dynamically-sized-byte-array), [Solidity Docs | String literals and types](https://docs.soliditylang.org/en/latest/types.html#string-literals-and-types)

Em Solidity, as strings são declaradas com a palavra-chave `string`.

Elas são strings de tamanho dinâmico codificadas em UTF-8.

```solidity
// SPDX-License-Identifier: GPLv3
pragma solidity ^0.8.0;

contract StringExample {
    string value = "hello world!";
    string value2 = unicode"happy christmas 🎅";
    string value3 = "\\\n\'\"\r\t\x00\u0000";
    string value4 = "first line\
second line\
third line";
    string value5 = "why" "can" "i" "do" "this?";

    function stringFunction() public pure returns (string memory) {
        return "hello from Solidity";
    }
}
```
