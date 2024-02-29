+++
title = "Ataques de Ultrapassagem (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-11-21T06:17:00-03:00
tags = ["solidity", "attack", "frontrun"]
draft = false
+++

tags
: [Padrões de Ataque (Solidity)]({{< relref "padroes_de_ataque_solidity.md" >}})

source
: [Frontrunning (SCSFG)](https://scsfg.io/hackers/frontrunning/), [Frontrunning Attacks (YT)](https://www.youtube.com/watch?v=DRZogmD647U&t=17134s)

Ataques de Ultrapassagem ou Frontrunning são ataques que têm como intuito:

-   Manipular a ordem de transações da Mempool.
-   Fazer a transação de um usuário ter perdas ou ser revertida (griefing) por ser ultrapassado na Mempool.
-   Conseguir melhores resultados para si mesmo.


## Como é feito {#como-é-feito}

Esses ataques são feitos aumentando o `base + priority` gas da sua transação para um `base + priority` gas maior que o da transação que deseja ultrapassar.


## Tipos {#tipos}

-   [Sandwich Attack (Solidity)]({{< relref "sandwich_attack_solidity.md" >}})


## Exemplos {#exemplos}


### Stake {#stake}

Vamos supor que apareça um token novo e o valor dele na pool é de $0.

-   Um usuário envia para a Mempool uma transação fazendo stake de $100.
-   Um usuário malicioso vê essa transação na Mempool, cria uma transação igual, porém, com mais gás e tem mais prioridade que a transação do outro usuário.
-   Esse mesmo usuário malicioso cria outra transação, com menos gás, para ser executada depois da transação do outro usuário, para fazer unstake.
-   O usuário malicioso sai ganhando em cima do stake do outro usuário.


### Order ID {#order-id}

Vamos supor que um protocolo use order IDs arbitrárias.

-   Um usuário cria uma transação com order ID 1.
-   Um usuário malicioso vê essa transação na Mempool e cria uma transação com o mesmo order ID, porém, com mais gas.
-   A transação do outro usuário é revertida.
