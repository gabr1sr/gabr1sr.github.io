+++
title = "Perpetuals (DeFi)"
author = ["Gabriel Rosa"]
date = 2023-11-20T09:38:00-03:00
draft = false
+++

tags
: [Finanças Descentralizadas (DeFi)]({{< relref "financas_descentralizadas_defi.md" >}})

source
: [Mission #1 - Perpetuals](https://guardianaudits.notion.site/Principles-Of-Testing-Smart-Contracts-4f3a77f6170147b6a07d5eef56c49bf0), [Advanced DeFi, Perpetuals Intro](https://www.youtube.com/watch?v=DRZogmD647U&t=11268s)

Perpetuals são uma forma de apostar no preço de um determinado token sem realmente comprar o token, enquanto o trader emprega alavancagem (employ leverage).


## Por que o nome? {#por-que-o-nome}

Perpetuals são chamadoes desta forma porque o trader pode manter sua posição "perpétua" aberta pelo tempo que quiser ou perpetuamente.


## O que é uma posição? {#o-que-é-uma-posição}

Podemos dizer que uma posição é uma aposta que o trader tem em aberto.

Uma posição é composta por:

-   ****Tamanho**** - quanto capital "virtual" o trader está comandando.
    -   Se uma posição é aberta em 1.5 BTC, se o preço subir, o trader consegue lucrar em cima dos 1.5 BTC.
-   ****Colateral**** - a quantidade de ativos utilizados para cobrir a posição do trader.
    -   Quando o trader perde dinheiro, essa perda é descontada do colateral.
    -   Se o colateral é insuficiente para cobrir as perdas, a posição é liquidada ou forçada a ser fechada.

O `tamanho / colateral` é a alavancagem (leverage) de uma posição.

Se uma posição é aberta com $10k de USDC como colateral e tamanho de $20k de BTC, minha alavancagem é de 2x.


## Direções de posição {#direções-de-posição}

Existem 2 tipos diferentes de direções que uma posição perpétua pode ter:

-   [Posição Longa (Perpetuals)]({{< relref "posicao_longa_perpetuals.md" >}})
-   [Posição Curta (Perpetuals)]({{< relref "posicao_curta_perpetuals.md" >}})
