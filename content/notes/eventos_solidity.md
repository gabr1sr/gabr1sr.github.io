+++
title = "Eventos (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-06
draft = false
+++

tags
: [Solidity]({{< relref "solidity.md" >}})

source
: [Digging deeper into Solidity's syntax](https://learnweb3.io/degrees/ethereum-developer-degree/sophomore/digging-deeper-into-soliditys-syntax/)

Eventos possibilitam os contratos fazerem logging de dados na blockchain. Logs de um contrato podem ser processados depois para fazer atualizações na interface front-end, por exemplo. Eles são comumente utilizados para possibilitar as interfaces front-end se atentarem a eventos específicos e atualizar a interface do usuário, ou usadas como uma forma barata de armazenamento.

```solidity
contract EventsExample {
    event TestCalled(address sender, string message);

    function test() public {
        emit TestCalled(msg.sender, "Someone called test()!");
    }
}
```
