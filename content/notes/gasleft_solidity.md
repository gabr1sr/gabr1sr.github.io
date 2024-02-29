+++
title = "Gasleft (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-12-13T14:29:00-03:00
draft = false
+++

tags
: [Solidity]({{< relref "solidity.md" >}})

source
: [Updraft Cyfrin | Calculate Withdraw gas costs](https://updraft.cyfrin.io/courses/foundry/foundry-fund-me/calculate-solidity-function-gas-costs?lesson_format=video)

Podemos utilizar a função `gasleft()` em Solidity para calcular o gas utilizado em alguma função.

Exemplo:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract GasleftExample {
    uint256 value = 123;

    function setValue(uint256 newValue) public {
        value = newValue;
    }

    function trackSetValue(uint256 newValue) public returns (uint256) {
        uint256 gasStart = gasleft();
        setValue(newValue);
        uint256 gasEnd = gasleft();
        return (gasStart - gasEnd) * tx.gasprice;
    }
}
```
