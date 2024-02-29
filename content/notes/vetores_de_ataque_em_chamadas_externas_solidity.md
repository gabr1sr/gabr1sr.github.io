+++
title = "Vetores de Ataque em Chamadas Externas (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-11-06T18:07:00-03:00
draft = false
+++

tags
: [Padrões de Ataque (Solidity)]({{< relref "padroes_de_ataque_solidity.md" >}})

source
: [External Call Safety (YT)](https://www.youtube.com/watch?v=DRZogmD647U&t=3808s)


## Ataques {#ataques}

Chamadas externas são os principais locais onde os ataques ocorrem.

Os principais assuntos a ter cuidado com chamadas externas são:

-   [Reentrada (SWC-107)]({{< relref "reentrada_swc_107.md" >}})
-   [Denial of Service (Solidity)]({{< relref "denial_of_service_solidity.md" >}})
