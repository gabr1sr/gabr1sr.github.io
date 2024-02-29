+++
title = "Transfer (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-11
tags = ["solidity", "syntax", "transfer"]
draft = false
+++

tags
: [Transferindo ETH (Solidity)]({{< relref "transferindo_eth_solidity.md" >}})

source
: [Digging deeper into Solidity's syntax](https://learnweb3.io/degrees/ethereum-developer-degree/sophomore/digging-deeper-into-soliditys-syntax/#eth-transfers)

Transferir ETH usando a função `transfer` não é o método atualmente recomendado. Apesar de ela reverter a transação em caso de falha, ela ainda é limitada a apenas 2300 gas para execução.

```solidity
contract SenderContract {
    function sendEther(address payable to) public payable {
        to.transfer(msg.value);
    }
}
```
