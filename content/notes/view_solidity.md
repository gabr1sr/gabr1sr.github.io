+++
title = "View (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-06
draft = false
+++

tags
: [Funções (Solidity)]({{< relref "funcoes_solidity.md" >}})

source
: [Introduction to Solidity](https://learnweb3.io/degrees/ethereum-developer-degree/freshman/introduction-to-solidity/)

São funções que não fazem nenhuma alteração de estados, mas lêem valores de estados.

```solidity
contract ViewExample {
    uint256 public x = 1;

    // Esta função não modifica o estado
    function addToX(uint256 y) public view returns (uint256) {
        return x + y;
    }
}
```
