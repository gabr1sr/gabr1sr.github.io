+++
title = "Boolean (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-26T04:33:00-03:00
draft = false
+++

tags
: [Tipos Básicos (Solidity)]({{< relref "tipos_basicos_solidity.md" >}})

source
: [Basic Solidity: Types](https://github.com/Cyfrin/foundry-full-course-f23#basic-solidity-types)

Em Solidity, valores boleanos são definidos com a palavra-chave `bool` e seu valor pode ser apenas `true` ou `false`.

```solidity
// SPDX-License-Identifier: GPLv3
pragma solidity ^0.8.21;

contract BooleanExample {
    bool trueValue = true;
    bool falseValue = false;
    bool defaultFalseValue;

    function boolFunction() public pure returns (bool) {
        return true;
    }
}
```
