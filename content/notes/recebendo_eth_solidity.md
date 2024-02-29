+++
title = "Recebendo ETH (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-07
draft = false
+++

tags
: [Funções (Solidity)]({{< relref "funcoes_solidity.md" >}})

source
: [Digging deeper into Solidity's syntax](https://learnweb3.io/degrees/ethereum-developer-degree/sophomore/digging-deeper-into-soliditys-syntax/#receiving-eth)

Para um contrato receber transferências de ETH diretamente, você precisa ter pelo menos uma destas funções declarads:

-   `receive() external payable` - que é chamada quando `msg.data` é um valor vazio
-   `fallback() external payable` - que é utilizada caso contrário

`msg.data` é uma forma de especificar dados arbitrários junto de uma transação. Você geralmente não vai usar ela manualmente.

```solidity
contract ReceiveEther {
    receive() external payable {}

    fallback() external payable {}

    function getBalance() public view returns (uint256) {
        return address(this).balance;
    }
}
```
