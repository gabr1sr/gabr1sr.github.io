+++
title = "Memory (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-12-08T10:53:00-03:00
draft = false
+++

tags
: [Locais de Dados (Solidity)]({{< relref "locais_de_dados_solidity.md" >}})

source
: [Updraft Cyfrin | Memory, storage and calldata](https://updraft.cyfrin.io/courses/solidity/simple-storage/solidity-memory-storage-calldata?lesson_format=transcript)

Em Solidity, `memory` é a palavra-chave para os dados que são guardados temporariamente na memória durante a execução de uma função.

Dados com a palavra-chave `memory` podem ser alteradas dentro do escopo da função.


## Exemplo {#exemplo}

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MemoryExample {
    string name;

    function setName(string memory newName) external {
        newName = string.concat(newName, "[new]");
        name = newName;
    }
}
```
