+++
title = "Reentrada (SWC-107)"
author = ["Gabriel Rosa"]
date = 2023-09-07
tags = ["reentrancy"]
draft = false
+++

tags
: [Vetores de Ataque em Chamadas Externas (Solidity)]({{< relref "vetores_de_ataque_em_chamadas_externas_solidity.md" >}})

source
: [Reentrancy vulnerabilities (Secureum)](https://github.com/x676f64/secureum-mind_map/blob/master/content/4.%20Pitfalls%20and%20Best%20Practices%20101/Reentrancy%20vulnerabilities.md), [Reentrancy (SWC-107)](https://swcregistry.io/docs/SWC-107/), [Reentrancy (SCSFG)](https://scsfg.io/hackers/reentrancy/#reentrancy), [Complete Reentrancy Guide (YT)](https://www.youtube.com/watch?v=DRZogmD647U&t=5775s)

É quando uma chamada externa arbitrária é feita quando as variáveis de estado utilizadas ainda não foram atualizadas e a função é chamada novamente antes de terminar sua execução.


## Tipos de Reentrada {#tipos-de-reentrada}

Seu comportamento pode variar de acordo com o tipo de reentrada:

-   [Reentrada de Função Única]({{< relref "reentrada_de_funcao_unica_solidity.md" >}})
-   [Reentrada Entre Funções]({{< relref "reentrada_entre_funcoes_solidity.md" >}})
-   [Reentrada de Somente-Leitura (Solidity)]({{< relref "reentrada_de_somente_leitura_solidity.md" >}})


## Como evitar {#como-evitar}

-   Certifique-se que todas as alterações de estados internas são feitas antes que a chamada seja executada. Isso é conhecido como Check-Effects-Interactions Pattern (CEI).
-   Use um bloqueador de reentrada ([OpenZeppelin's ReentrancyGuard](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/security/ReentrancyGuard.sol), por exemplo).
