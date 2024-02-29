+++
title = "Construtores (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-06
draft = false
+++

tags
: [Funções (Solidity)]({{< relref "funcoes_solidity.md" >}})

source
: [Digging deeper into Solidity's syntax](https://learnweb3.io/degrees/ethereum-developer-degree/sophomore/digging-deeper-into-soliditys-syntax/)

Um `construtor` é uma função opcional que é executada quando o contrato é primeiramente deployado. Você pode também passar argumentos em construtores.

```solidity
contract ConstructorExample {
    string public name;

    constructor(string memory _name) {
        name = _name;
    }
}
```
