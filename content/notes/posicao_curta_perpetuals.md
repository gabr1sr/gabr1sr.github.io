+++
title = "Posição Curta (Perpetuals)"
author = ["Gabriel Rosa"]
date = 2023-11-20T10:18:00-03:00
draft = false
+++

tags
: [Perpetuals (DeFi)]({{< relref "perpetuals_defi.md" >}})

source
: [Mission #1 - Perpetuals](https://guardianaudits.notion.site/Principles-Of-Testing-Smart-Contracts-4f3a77f6170147b6a07d5eef56c49bf0)

É a posição em que o trader:

-   lucra quando o preço do token desce.
-   perde quando o preço do token sobe.


## Exemplo {#exemplo}

-   ****O preço atual do ETH é $5.000.****
-   ****A alavancagem (leverage) máxima permitida antes de liquidar é de 15x.****
-   ****Bob abre uma posição curta com $1.000 de USDC como colateral e $10.000 de tamanho.****
    No preço atual do ETH, seus $10.000 de tamanho são convertidos em 2 ETH de tamanho em tokens para a posição.
-   ****A alavancagem de Bob é de 10x.****
-   ****O preço do ETH cai para $4.000.****
    Uma diminuição de 20%.
-   ****Bob lucrou! Sua posição perpétua de 2 ETH de tamanho em tokens e sua base de custo foram $5.000.****
    Logo, seu PnL é de `($5.000 - $4.000) * 2 = $2.000` ou `(Preço Médio da Posição - Preço Atual de Mercado) * Tamanho em Tokens`.
-   ****Bob poderia fechar sua posição e obter os $2.000 de lucro, mas como o Bob é avarento, ele irá manter aberta para tentar obter mais lucro.****
-   ****Inevitavelmente, o preço do ETH sobe para $5.250.****
-   ****Os ganhos de Bob evaporaram! Agora, ele está em prejuízo.****
    Sua posição perpétua agora tem o seguinte PnL: `($5.000 - $5.250) * 2 = -$500`.
-   ****Esses $500 de prejuízo são cobertos pelo colateral de Bob.****
    Isso significa que seu colateral restante é de: `$1.000 - $500 = $500`.
    Bob agora tem apenas $500 de colateral restante para tentar recuperar sua posição.
    Portanto, sua alavancagem é igual a seus $10.000 de tamanho original dividido por seus $500 restantes de colateral:
    `$10.000 / $500 = 20x`.
-   ****A posição de Bob ultrapassa o limite de liquidação e, portanto, ele é liquidado.****
    Seus colaterais são confiscados, seu prejuízo de $500 é enviado os provedores de liquidez junto com uma taxa adicional de liquidação, seus colaterais restantes são mandados de volta para ele.
