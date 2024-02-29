+++
title = "Send (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-11
tags = ["solidity", "syntax", "transfer"]
draft = false
+++

tags
: [Transferindo ETH (Solidity)]({{< relref "transferindo_eth_solidity.md" >}})

source
: [Digging deeper into Solidity's syntax](https://learnweb3.io/degrees/ethereum-developer-degree/sophomore/digging-deeper-into-soliditys-syntax/#eth-transfers)

Podemos transferir ETH usando a função `send`, mas não é uma opção recomendada, pois só pode gastar até 2300 gas para transferir ETH e, por mais que a execução falhe, ela não irá dar erro, apenas irá retornar `false`.

```solidity
contract SenderContract {
  function sendEther(address payable to) public payable {
      bool sent = to.send(msg.value);
      require(sent, "Failed to send ETH");
    }
  }
```
