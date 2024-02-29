+++
title = "Modificadores de Funções (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-06
draft = false
+++

tags
: [Funções (Solidity)]({{< relref "funcoes_solidity.md" >}})

source
: [Digging deeper into Solidity's syntax](https://learnweb3.io/degrees/ethereum-developer-degree/sophomore/digging-deeper-into-soliditys-syntax/)

Modificadores são códigos que podem rodar antes e/ou depois de uma chamada de função. Eles são comumente utilizados para restringir acesso a certas funções, validar parâmetros de entrada, proteger contra certos tipos de ataques, etc.

```solidity
contract ModifiersExample {
    address public owner;

    constructor() {
        owner = msg.sender;
    }

    modifier onlyOwner() {
        require(msg.sender == owner, "You are not the owner");

        // O Underline é um caractere especial usado dentro de modificadores.
        // Ele avisa ao Solidity para executar a função em que o modificador foi usado
        // Nesse ponto.
        // Antes disso, o modificador vai primeiro performar o código que está acima
        // e então rodar o restante do código (caso o require não dê erro).
        _;
    }

    function changeOwner(address _newOwner) public onlyOwner {
        owner = _newOwner;
    }
}
```
