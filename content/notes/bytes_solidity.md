+++
title = "Bytes (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-12-07T22:57:00-03:00
draft = false
+++

tags
: [Tipos Básicos (Solidity)]({{< relref "tipos_basicos_solidity.md" >}})

source
: [Updraft Cyfrin | Basic variable types](https://updraft.cyfrin.io/courses/solidity/simple-storage/solidity-basic-types?lesson_format=transcript), [Solidity Docs | Fixed-size byte arrays](https://docs.soliditylang.org/en/latest/types.html#fixed-size-byte-arrays), [Solidity Docs | Dynamically-sized byte array](https://docs.soliditylang.org/en/latest/types.html#dynamically-sized-byte-array)

Em Solidity, os bytes são declarados com a palavra-chave `bytes` sozinha ou `bytes` mais o número de bytes na frente;

O número de bytes pode ser: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31 ou 32.

O menor valor é 0 e o maior valor é `(2^(bytes * 8)) - 1`.


## Array de bytes de tamanho fixo {#array-de-bytes-de-tamanho-fixo}

Quando especificamos um número depois da palavra-chave `bytes`, estamos criando um byte array de tamanho fixo.

```solidity
// SPDX-License-Identifier: GPLv3
pragma solidity ^0.8.0;

contract FixedSizeByteArrayExample {
    bytes32 value1 = "hello";
    bytes32 value2 = bytes32(uint256(0xffff));
    bytes32 value3 = "\xff\xff";
    bytes32 maxValue = bytes32(type(uint256).max);
    bytes32 minValue = bytes32(type(uint256).min);
    bytes32 defaultValueZero;

    function bytes32Function() public pure returns (bytes32) {
        return "\xde\xad\xbe\xef";
    }
}
```


## Array de bytes de tamanho dinâmico {#array-de-bytes-de-tamanho-dinâmico}

Quando não especificamos um número depois da palavra-chave `bytes`, estamos criando um byte array de tamanho dinâmico.

```solidity
// SPDX-License-Identifier: GPLv3
pragma solidity ^0.8.0;

contract DynamicSizeByteArrayExample {
    bytes value1 = "hello";
    bytes value2 = bytes("world");
    bytes value3 = abi.encodePacked("hello world");

    function bytesFunction() public pure returns (bytes memory) {
        return hex"deadbeef";
    }
}
```
