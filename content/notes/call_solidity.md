+++
title = "Call (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-11
tags = ["solidity", "syntax", "transfer"]
draft = false
+++

tags
: [Transferindo ETH (Solidity)]({{< relref "transferindo_eth_solidity.md" >}})

source
: [Digging deeper into Solidity's syntax](https://learnweb3.io/degrees/ethereum-developer-degree/sophomore/digging-deeper-into-soliditys-syntax/#eth-transfers)

Transferir ETH utilizando a função `call` é o método recomendado e mais utilizado atualmente. Ela é uma função low-level que transfere ETH e encaminha todo o gas restante junto, removendo o limite de 2300 gas. Além disso, a transação não reverte automaticamente se falhar, apenas retorna `false`.

```solidity
contract SenderContract {
    function sendEther(address payable to) public payable {
        (bool sucess, /*bytes memory data*/) = to.call{value: msg.value}("");
        require(success, "Failed to send ETH");
    }
}
```
