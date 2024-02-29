+++
title = "UUPS Proxy Pattern (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-20
draft = false
+++

tags
: [Padrões de Proxy (Solidity)]({{< relref "padroes_de_proxy_solidity.md" >}})

source
: [Building smart contracts that can be upgraded over time](https://learnweb3.io/lessons/building-smart-contracts-that-can-be-upgraded-over-time/)

É uma outra forma de separar as responsabilidades entre os contratos de **Proxy** e de **Implementação**.

Nesse caso, a função `upgradeTo` faz parte do contrato de **Implementação** e é chamado usando um `delegatecall` através do **Proxy**, pelo owner.

Nesse pattern, seja admin ou usuário, todas as chamadas são enviadas para o Contrato de **Implementação**. A vantagem disso é que toda vez que uma chamada for feita, não há a necessidade de checar se quem iniciou essa chamada é admin ou não, assim melhorando a eficiência e diminuindo custos. Outra vantagem é que você pode customizar funções do Contrato de **Implementação** de acordo com as suas necessidades, adicionando coisas como, por exemplo, **Timelock**, **Access Control**, etc. com cada nova **Implementação** que é feita, coisa que não é possível fazer com o [Transparent Proxy Pattern (Solidity)]({{< relref "transparent_proxy_pattern_solidity.md" >}}).


## Problemas {#problemas}

O problema agora é que a função `upgradeTo` existe no lado do Contrato de **Implementação** e, por conta disso, o desenvolvedor tem que se preocupar em como essa função é implementada, o que às vezes pode ser complicado porque mais código é adicionado e isso pode aumentar a possibilidade de ataques. Essa função também precisa estar em todas as versões do Contrato de **Implementação**, o que introduz um risco se o desenvolvedor se esquecer de adicionar essa função.
