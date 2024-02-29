+++
title = "Public (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-06
draft = false
+++

tags
: [Funções (Solidity)]({{< relref "funcoes_solidity.md" >}})

source
: [Introduction to Solidity](https://learnweb3.io/degrees/ethereum-developer-degree/freshman/introduction-to-solidity/)

Modificador de visibilidade para variáveis e funções que faz com que ela possa ser chamada tanto por usuários e contratos externos quanto pelo próprio contrato em que ela está.

```solidity
contract PublicExample {
    // Essa é uma variável pública
    uint256 public value;

    // Essa é uma função pública
    function getValue() public view returns (uint256) {
        return value;
    }
}
```
