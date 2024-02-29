+++
title = "Princípios de Testes de Contratos Inteligentes (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-11-20T06:53:00-03:00
draft = false
+++

tags
: [Solidity]({{< relref "solidity.md" >}})

source
: [Principles Of Smart Contract Testing (YT)](https://www.youtube.com/watch?v=DRZogmD647U&t=7413s). [Principles Of Smart Contract Testing](https://guardianaudits.notion.site/Principles-Of-Testing-Smart-Contracts-4f3a77f6170147b6a07d5eef56c49bf0)


## Testes Gerais {#testes-gerais}

-   Tentar atingir 100% de code coverage
-   100% de coverage não garante 100% de segurança
-   Cobrir não somente um comportamento esperado, mas todo comportamento que possa acontecer


## Unit Tests {#unit-tests}

-   Detectar bugs enquanto o projeto está sendo desenvolvido
-   Implementar para funções individuais


## Integration Tests {#integration-tests}

-   Detectar bugs na hora de testar o projeto todo
-   Interagir com o sistema como um usuário interagiria


## Fuzz Tests {#fuzz-tests}

-   Detectar bugs usando valores aleatórios inúmeras vezes
-   Bons candidatos são funções com cálculos e matemática complexa
-   Echidna


## Invariant Tests {#invariant-tests}

-   Garantir que valores importantes não darão erro
-   Geralmente utilizados em valores unchecked, ou que não podem dar underflow, ou específicos de protocolos


## Path Independence {#path-independence}

São casos em que o resultado é o mesmo independente da ordem dos acontecimentos.

Vamos supor os seguintes acontecimentos no contexto de um ERC20:

-   Bob transfere 20 DAI para Alice
-   Charlie transfere 20 DAI para Alice

Não importa a ordem que aconteça, o resultado sempre será o mesmo.


## Path Dependence {#path-dependence}

São casos em que o resultado depende da ordem dos acontecimentos.

Vamos supor os seguintes acontecimentos no contexto de um AMM:

-   Bob compra BTC a $50.000
-   Alice compra BTC a $50.010

Nesta ordem, Bob acaba ficando com mais BTC do que Alice.

Porém, se invertemos a ordem, Alice acaba ficando com mais BTC do que Bob.
