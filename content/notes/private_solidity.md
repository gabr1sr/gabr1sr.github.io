+++
title = "Private (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-06
draft = false
+++

tags
: [Funções (Solidity)]({{< relref "funcoes_solidity.md" >}})

source
: [Access private data in smart contracts](https://learnweb3.io/degrees/ethereum-developer-degree/senior/access-private-data-in-smart-contracts/)

Modificador de visibilidade para funções e variáveis que faz com que ela possa ser chamada e modificada apenas pelo contrato em que ela está.

```solidity
contract PrivateExample {
    // Esta é uma variável privada
    uint256 private _value;

    // Esta é uma função privada
    function _getValue() private view returns (uint256) {
        return _value;
    }
}
```
