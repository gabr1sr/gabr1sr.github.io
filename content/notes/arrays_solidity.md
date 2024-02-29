+++
title = "Arrays (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-12-08T10:14:00-03:00
draft = false
+++

tags
: [Tipos Básicos (Solidity)]({{< relref "tipos_basicos_solidity.md" >}})

source
: [Updraft Cyfrin | Arrays and structs](https://updraft.cyfrin.io/courses/solidity/simple-storage/solidity-arrays-and-structs?lesson_format=video), [Solidity Docs | Array Members](https://docs.soliditylang.org/en/latest/types.html#array-members)

Em Solidity, podemos declarar arrays das seguintes formas:

-   `T[]` =&gt; array do tipo `T` com tamanho dinâmico.
-   `T[<size>]` =&gt; array do tipo `T` com tamanho fixo (`<size>` de tamanho).


## Membros {#membros}

-   `length` =&gt; retorna o tamanho do array.
-   `push()` =&gt; adiciona um valor iniciado em zero ao final do array e retorna uma referência ao último elemento do array.
-   `push(x)` =&gt; adiciona o valor `x` ao final do array e retorna nada.
-   `pop()` =&gt; remove um elemento do final do array e retorna nada.


## Acessar Elementos {#acessar-elementos}

Podemos acessar elementos específicos do array através de array subscripting: `<array>[<index>]`.

Para pegar o elemento de índice `5` de um array, fazemos isto, por exemplo: `array[5]`.


## Slices {#slices}

Podemos criar um slice de array através da síntaxe: `<array>[<start>:<end>]`.

Para criarmos um slice de array do elemento de índice `5` até o final, fazemos isto: `array[5:]`.

Para o primeiro elemento até o elemento de índice `5`, fazemos isto: `array[:5]`.

Para o elemento de índice `x` até o elemento de índice `y`, fazemos isto: `array[x:y]`.


## Exemplos {#exemplos}

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract ArrayExample {
    address[] dynamicAddresses;
    uint256[5] fiveUint256s;

    function addAddress(address newAddress) public {
        dynamicAddresses.push(newAddress);
    }

    function addUint256(uint256 index, uint256 newUint256) public {
        fiveUint256s[index] = newUint256;
    }

    function firstAddress() public view returns (address) {
        return dynamicAddresses[0];
    }

    function firstUint256() public view returns (uint256) {
        return fiveUint256s[0];
    }
}
```
