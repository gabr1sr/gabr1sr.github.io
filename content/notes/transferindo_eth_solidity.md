+++
title = "Transferindo ETH (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-07
tags = ["solidity", "syntax", "transfer"]
draft = false
+++

tags
: [Solidity]({{< relref "solidity.md" >}})

source
: [Digging deeper into Solidity's syntax](https://learnweb3.io/degrees/ethereum-developer-degree/sophomore/digging-deeper-into-soliditys-syntax/#eth-transfers), [Sending Ether (transfer, send, call)](https://solidity-by-example.org/sending-ether/)

Existem 3 formas de transferir ETH de um contrato para outro endereço. Entretanto, 2 delas não são métodos recomendados:

-   [método send]({{< relref "send_solidity.md" >}})
-   [método transfer]({{< relref "transfer_solidity.md" >}})

E 1 delas é a forma atualmente recomendada:

-   [método call]({{< relref "call_solidity.md" >}})
