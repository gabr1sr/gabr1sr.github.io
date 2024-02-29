+++
title = "Storage (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-12-08T10:58:00-03:00
draft = false
+++

tags
: [Locais de Dados (Solidity)]({{< relref "locais_de_dados_solidity.md" >}})

source
: [Updraft Cyfrin | Memory, storage and calldata](https://updraft.cyfrin.io/courses/solidity/simple-storage/solidity-memory-storage-calldata?lesson_format=transcript)

Em Solidity, `storage` é a palavra-chave para os dados que são guardados permanentemente dentro do contrato.

Esses dados podem ser alterados e, dentro de funções, podemos criar ponteiros para dados guardados na `storage`.


## Exemplo {#exemplo}

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract StorageExample {
    struct Person {
        string name;
        uint256 age;
    }

    mapping(address => Person) persons;

    function addPerson(string calldata name, uint256 age) external {
        persons[msg.sender] = Person(name, age);
    }

    function changePerson(address target, string calldata name, uint256 age) external {
        Person storage person = persons[target]; // ponteiro
        person.name = name;
        person.age = age;
    }
}
```
