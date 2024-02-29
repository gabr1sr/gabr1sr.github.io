+++
title = "Pure (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-06
draft = false
+++

tags
: [Funções (Solidity)]({{< relref "funcoes_solidity.md" >}})

source
: [Introduction to Solidity](https://learnweb3.io/degrees/ethereum-developer-degree/freshman/introduction-to-solidity/)

São funções que não fazem nenhuma alteração de estados e nem lêem valores de estados.

```solidity
contract PureExample {
    // Esta função não modifica e nem lê o estado
    function add(uint256 x, uint256 y) public pure returns (uint256) {
        return x + y;
    }
}
```
