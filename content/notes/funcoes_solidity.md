+++
title = "Funções (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-12-08T08:35:00-03:00
draft = false
+++

tags
: [Solidity]({{< relref "solidity.md" >}})

source
: [Updraft Cyfrin | Functions](https://updraft.cyfrin.io/courses/solidity/simple-storage/solidity-functions), [Solidity Docs | Function Types](https://docs.soliditylang.org/en/latest/types.html#function-types), [Solidity Docs | Function Declaration](https://docs.soliditylang.org/en/latest/style-guide.html#function-declaration), [Solidity Docs | Order of Functions](https://docs.soliditylang.org/en/latest/style-guide.html#order-of-functions), [Solidity Docs | Function Visibility](https://docs.soliditylang.org/en/latest/contracts.html#function-visibility), [Solidity | State Mutability](https://docs.soliditylang.org/en/latest/contracts.html#state-mutability), [LearnWeb3 | Introduction to Solidity](https://learnweb3.io/degrees/ethereum-developer-degree/freshman/introduction-to-solidity), [LearnWeb3 | Digging deeper into Solidity's syntax](https://learnweb3.io/degrees/ethereum-developer-degree/sophomore/digging-deeper-into-soliditys-syntax), [LearnWeb3 | Access private data in smart contracts](https://learnweb3.io/lessons/access-private-data-in-smart-contracts)

Em Solidity, podemos declarar funções através da palavra-chave `function`.


## Síntaxe {#síntaxe}

A síntaxe para declaração de função é a seguinte:

`function <functionName>(<parameter types>) {public|private|internal|external} [pure|view|payable] [returns (<return types>)]`


## Ordenação e Agrupamento {#ordenação-e-agrupamento}


### Ordem de Modificadores {#ordem-de-modificadores}

Os modificadores devem seguir a seguinte ordem:

-   Visibilidade
-   Mutabilidade
-   Virtual
-   Override
-   Modificadores customizados


### Agrupamento de Funções {#agrupamento-de-funções}

As funções devem ser agrupadas na seguinte ordem:

-   constructor
-   receive function (se existir)
-   fallback function (se existir)
-   external
-   public
-   internal
-   private

`view` e `pure` por último nesses agrupamentos.


## Modificadores {#modificadores}


### Modificadores de Visibilidade {#modificadores-de-visibilidade}

-   [Public (Solidity)]({{< relref "public_solidity.md" >}})
-   [Private (Solidity)]({{< relref "private_solidity.md" >}})
-   [External (Solidity)]({{< relref "external_solidity.md" >}})
-   [Internal (Solidity)]({{< relref "internal_solidity.md" >}})

Caso não especificado, ela será `internal` por padrão.


### Modificadores de Mutabilidade {#modificadores-de-mutabilidade}

-   [View (Solidity)]({{< relref "view_solidity.md" >}})
-   [Pure (Solidity)]({{< relref "pure_solidity.md" >}})


### Modificadores de Substituição {#modificadores-de-substituição}

-   [Virtual (Solidity)]({{< relref "virtual_solidity.md" >}})
-   [Override (Solidity)]({{< relref "override_solidity.md" >}})


### Modificadores Customizados {#modificadores-customizados}

-   [Modificadores de Funções (Solidity)]({{< relref "modificadores_de_funcoes_solidity.md" >}})


## Funções Especiais {#funções-especiais}

-   [Construtores (Solidity)]({{< relref "construtores_solidity.md" >}})
-   [Recebendo ETH (Solidity)]({{< relref "recebendo_eth_solidity.md" >}}) (receive e fallback)


## Exemplos {#exemplos}

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract FunctionExample {
    uint256 stateVariable1;

    constructor(uint256 stateVariable1_) {
        stateVariable1 = stateVariable1_;
    }

    receive() external payable {}

    fallback() external payable {}

    function foo() external pure returns (string memory) {
        return "foo";
    }

    function getStateVariable1() public view returns (uint256) {
        return stateVariable1;
    }

    function hello() public pure returns (string memory) {
        return "hello";
    }

    function _world() internal pure returns (string memory) {
        return "world";
    }

    function _helloWorld() private pure returns (string memory) {
        return string.concat(hello(), " ", _world(), "!");
    }
}
```
