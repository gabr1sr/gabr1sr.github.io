+++
title = "Imports (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-12-08T11:33:00-03:00
draft = false
+++

tags
: [Solidity]({{< relref "solidity.md" >}})

source
: [Updraft Cyfrin | Solidity imports](https://updraft.cyfrin.io/courses/solidity/storage-factory/solidity-imports?lesson_format=video), [Solidity Docs | Syntax and Semantics](https://docs.soliditylang.org/en/latest/layout-of-source-files.html#syntax-and-semantics)

Em Solidity, podemos importar códigos das seguintes formas:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "filename";
```

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import * as symbolName from "filename";
```

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "filename" as symbolName;
```

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import {symbol1 as alias, symbol2} from "filename";
```
