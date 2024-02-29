+++
title = "Sandwich Attack (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-11-21T06:57:00-03:00
draft = false
+++

tags
: [Ataques de Ultrapassagem (Solidity)]({{< relref "ataques_de_ultrapassagem_solidity.md" >}})

source
: [Sandwich Attacks (YT)](https://www.youtube.com/watch?v=DRZogmD647U&t=18561s)

Sandwich Attack ou Ataque Sanduíche é um tipo de ataque que:

-   Combina front-running e back-running.
-   Tira vantagem copiando uma transação, alterando uma variável e executando-na antes dessa transação.
-   E cria outra transação logo após a transação que foi copiada.


## Exemplo {#exemplo}

Uma liquidity pool tem 400 Token A e 200 Token B.

Um usuário deseja fazer swap de 50 Token B.

O usuário malicioso, que performa o sandwich attack, copia essa transação, adiciona mais gás para ultrapassar a transação do outro usuário e faz swap de 100 Token B ao invés de 50 Token B.

O valor do Token B na liquidity pool aumenta e o valor de Token A que o primeiro usuário recebe será menor do que o esperado.

A transação do usuário malicioso acontece primeiro e a do primeiro usuário acontece logo após.

O usuário malicioso vai e faz swap do Token A para o Token B e recebe mais Token B do que ele trocou anteriormente.

O primeiro usuário sofre prejuízo.


## Mitigação {#mitigação}

Adicionar % de slippage.

Usar Flashbots para não tomar frontrun.
