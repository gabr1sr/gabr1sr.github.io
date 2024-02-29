+++
title = "Transparent Proxy Pattern (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-20
draft = false
+++

tags
: [Padrões de Proxy (Solidity)]({{< relref "padroes_de_proxy_solidity.md" >}})

source
: [Building smart contracts that can be upgraded over time](https://learnweb3.io/lessons/building-smart-contracts-that-can-be-upgraded-over-time/)

    É uma forma simples de separar as responsabilidades entre os contratos de **Proxy** e de **Implementação**.

Nesse caso, a função `upgradeTo` é parte do contrato de **Proxy** e a **Implementação** pode ser atualizada chamando a função `upgradeTo` no proxy.

Porém, existem algumas ressalvas.

Pode existir um caso onde o Contrato **Proxy** e o Contrato de **Implementação** têm uma função com o mesmo nome e argumentos. Imagine que tanto o Contrato **Proxy** quanto o de **Implementação** têm uma função chamada `owner()`. Os contratos de **Proxy** Transparente, esse problema é resolvido pelo contrato **Proxy** que decide se uma chamada feita pelo usuário vai executar dentro do Contrato **Proxy** ou dentro do Contrato de **Implementação** baseado na variável global `msg.sender`.


## Problemas {#problemas}

Como nós sabemos, o endereço do `owner` terá que ser guardado na storage e usar a storage é uma das formas mais ineficientes e custosas. Quando interagimos com um contrato inteligente, toda vez que o usuário chamar o proxy, o proxy checa se o usuário é o admin ou não, o que adiciona custo desnecessário de gas para a maioria das funções do contrato.
