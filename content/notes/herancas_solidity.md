+++
title = "Heranças (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-06
draft = false
+++

tags
: [Solidity]({{< relref "solidity.md" >}})

source
: [Digging deeper into Solidity's syntax](https://learnweb3.io/degrees/ethereum-developer-degree/sophomore/digging-deeper-into-soliditys-syntax/)

Herança é o procedimento onde um contrato pode herdar os atributos e métodos de outro contrato. Solidity suporta múltipla herança. Contratos podem herdar outros contratos utilizando a palavra-chave `is`.

Um contrato-pai que tem uma ou mais funções que podem ser sobrescritas (overridden) por um contrato-filho devem ser declaradas como `virtual`.

Um contrato-filho deve usar a palavra-chave `override` quando for sobrescrever uma função herdada.

A ordem de herança depende se os contratos-pai compartilham os métodos ou atributos de mesmo nome. Se os atributos e métodos forem iguais, a parente mais à direita vai ser o mais importante.

```solidity
contract A {
    function foo() public pure virtual returns (string memory) {
        return "A";
    }
}

contract B is A {
    function foo() public pure virtual override returns (string memory) {
        return "B";
    }
}

contract C is A {
    function foo() public pure virtual override returns (string memory) {
        return "C";
    }
}

contract D is B, C {
    // D.foo() retorna "C"
    function foo() public pure override(B, C) returns (string memory) {
        return super.foo();
    }
}

contract E is C, B {
    // E.foo() retorna "B"
    function foo() public pure override(C, B) returns (string memory) {
        return super.foo();
    }
}
```
