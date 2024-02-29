+++
title = "Override (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-12-08T09:07:00-03:00
draft = false
+++

tags
: [Funções (Solidity)]({{< relref "funcoes_solidity.md" >}})

source
: [Solidity Docs | Function Overriding](https://docs.soliditylang.org/en/latest/contracts.html#function-overriding)

A palavra-chave `override` é um modificador utilizado para sobrescrever funções ou modificadores.

Funções ou modificadores sobrescritos devem ter sido declarados usando a palavra-chave [Virtual (Solidity)]({{< relref "virtual_solidity.md" >}}).

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

contract OverrideExample is VirtualExample {
    modifier onlyOwner() override {
        require(msg.sender == owner && owner != address(0));
        _;
    }

    function transferOwnership(address newOwner) external override onlyOwner {
        require(newOwner != address(0));
        owner = newOwner;
    }
}
```

```solidity
// SPDX-License-Identifier: GPL-3.0
pragma solidity >=0.6.0 <0.9.0;

contract Base1 {
    function foo() virtual public {}
}

contract Base2 {
    function foo() virtual public {}
}

contract Inherited is Base1, Base2 {
    function foo() public override(Base1, Base2) {}
}
```
