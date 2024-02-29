+++
title = "Internal (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-06
draft = false
+++

tags
: [Funções (Solidity)]({{< relref "funcoes_solidity.md" >}})

source
:

Modificador de visibilidade para funções que faz com que ela possa ser chamada apenas pelo próprio contrato em que ela está. Contratos que derivam deste podem chamar funções internas herdadas.

```solidity
contract InternalExample {
    // Esta é uma função interna
    function getValue() internal view returns (string memory) {
        return "Posso ser chamado apenas pelo contrato em que estou o que deriva de mim!";
    }
}

contract InternalExampleChild is InternalExample {
    function showValue() public view returns (string memory) {
        return getValue();
    }
}
```
