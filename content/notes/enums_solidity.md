+++
title = "Enums (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-06
draft = false
+++

tags
: [Tipos Definidos pelo Usuário (Solidity)]({{< relref "tipos_definidos_pelo_usuario_solidity.md" >}})

source
: [Digging deeper into Solidity's syntax](https://learnweb3.io/degrees/ethereum-developer-degree/sophomore/digging-deeper-into-soliditys-syntax/#enums)

A palavra **Enum** se refere a **Enumerable**. Eles são tipos definidos pelo usuário que contém nomes legíveis para um conjunto de constantes, chamados membros. Eles são comumente utilizados para restringir uma variável a apenas um conjunto de valores pré-definidos. Já que eles são apenas uma abstração para constantes legíveis, na realidade, eles são internamente representados como `uint`.

```solidity
contract Enum {
    enum Status {
        Pending,    // 0
        Shipped,    // 1
        Accepted,   // 2
        Rejected,   // 3
        Canceled    // 4
    }

    Status public status;

    function get() public view returns (Status) {
        return status;
    }

    function set(Status _status) public {
        status = _status;
    }

    function cancel() public {
        status = Status.Canceled;
    }
}
```
