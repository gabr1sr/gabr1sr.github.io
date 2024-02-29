+++
title = "Virtual (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-12-08T09:02:00-03:00
draft = false
+++

tags
: [Funções (Solidity)]({{< relref "funcoes_solidity.md" >}})

source
: [Solidity Docs | Function Overriding](https://docs.soliditylang.org/en/latest/contracts.html#function-overriding)

A palavra-chave `virtual` é um modificador utilizado para marcar funções ou modificadores que podem ser sobrescritos.

Essas funções e modificadores podem ser sobrescritos utilizando a palavra-chave [Override (Solidity)]({{< relref "override_solidity.md" >}}).

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract VirtualExample {
    address owner;

    modifier onlyOwner() virtual {
        require(msg.sender == owner);
        _;
    }

    function transferOwnership(address newOwner) external virtual onlyOwner {
        owner = newOwner;
    }
}
```
