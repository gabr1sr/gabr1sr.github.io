+++
title = "Calldata (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-12-08T10:56:00-03:00
draft = false
+++

tags
: [Locais de Dados (Solidity)]({{< relref "locais_de_dados_solidity.md" >}})

source
: [Updraft Cyfrin | Memory, storage and calldata](https://updraft.cyfrin.io/courses/solidity/simple-storage/solidity-memory-storage-calldata?lesson_format=transcript)

Em Solidity, `calldata` é a palavra-chave para os dados que são guardados temporariamente na chamada durante a execução de uma função.

Dados com a palavra-chave `calldata` não podem ser alterados.


## Exemplo {#exemplo}

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract CalldataExample {
    string name;

    function setName(string calldata newName) external {
        name = newName;
    }
}
```
