+++
title = "External (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-06
draft = false
+++

tags
: [Solidity]({{< relref "solidity.md" >}})

source
:

Modificador de visibilidade para funções que faz com que ela possa ser chamada apenas por usuários ou contratos externos.

```solidity
contrtact ExternalExample {
    // Esta é uma função externa
    function getValue() external view returns (string memory) {
        return "Posso ser chamado apenas por usuários ou contratos externos!";
    }
}
```
