+++
title = "Posição Longa (Perpetuals)"
author = ["Gabriel Rosa"]
date = 2023-11-20T09:50:00-03:00
draft = false
+++

tags
: [Perpetuals (DeFi)]({{< relref "perpetuals_defi.md" >}})

source
: [Mission #1 - Perpetuals](https://guardianaudits.notion.site/Principles-Of-Testing-Smart-Contracts-4f3a77f6170147b6a07d5eef56c49bf0)

É a posição em que o trader:

-   lucra quando o preço do token sobe.
-   perde quando o preço do token desce.


## Fórmula PnL {#fórmula-pnl}

`(Preço Atual do Token - Preço de Quando Comprou o Token) * Quantidade do Token`


## Exemplo {#exemplo}

-   ****O preço atual do ETH é de $5.000.****
-   ****A alavancagem (leverage) máxima permitida antes de liquidar é 15x.****
-   Bob abre uma posição longa com $1.000 USDC como colateral e $10.000 de tamanho.
    No preço atual do ETH, seus $10.000 de tamanho convertem para 2 ETH de tamanho em tokens para a posição.
-   ****Bob tem $10.000 de tamanho e apenas $1.000 de colateral.****
    Portanto, a alavancagem (leverage) da posição de Bob é 10x, o que está dentro da faixa permitida.
-   ****O preço do ETH sobe para $6.000.****
    Um aumento de 20%.
-   ****Bob lucrou! Sua posição perpétua tem 2 ETH de tamanho em tokens e sua base de custo foi $5.000.****
    Logo, seu PnL (profit and lost) é `($6.000 - $5.000) * 2 = $2.000` ou `(Preço Atual de Mercado - Preço Médio da Posição) * Tamanho em Tokens`.
-   ****Bob pode fechar sua posição e obter os $2.000 de lucro, mas Bob é avarento e decide manter sua posição aberta para tentar lucrar ainda mais.****
-   ****Inevitavelmente, o preço do ETH cai para $4.750.****
-   ****O lucro de Bob evaporou e agora ele está em prejuízo!****
    Sua posição perpétua agora tem o seguinte PnL: `($4.750 - $5.000) * 2 = -$500`
-   ****Esse prejuízo de $500 é coberto pelo colateral de Bob.****
    Isso significa que seu colateral restante é: `$1.000 - $500 = $500`.
    Bob agora tem apenas $500 de colateral restantes para recuperar o prejuízo.
    Portanto, sua alavancagem é seus $10.000 de tamanho original dividido por seus $500 de colateral restantes:
    `$10.000 / $500 = 20x`
-   ****A posição de Bob ultrapassa o limite de liquidação. Portanto, ela será liquidada.****
    Seu colateral é pego pelo protocolo, seus $500 de prejuízo são mandados para os provedores de liquidez junto com uma taxa adicional de liquidação, seus colaterais restantes são mandados de volta para ele.
