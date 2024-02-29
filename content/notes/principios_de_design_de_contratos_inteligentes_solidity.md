+++
title = "Princípios de Design de Contratos Inteligentes (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-10-25T20:57:00-03:00
draft = false
+++

tags
: [Solidity]({{< relref "solidity.md" >}})

source
: [Principles Of Smart Contract Design (YT)](https://www.youtube.com/watch?v=DRZogmD647U&t=1011s), [Principles Of Designing Secure Smart Contracts (Guardian Audits)](https://guardianaudits.notion.site/Principles-Of-Designing-Secure-Smart-Contracts-8082b2fc0d6942f7956a5aa072654d14)

1:26:25


## Princípios {#princípios}


### Quanto menos código melhor {#quanto-menos-código-melhor}

Quanto menos linhas de código o contrato inteligente tiver, menor vai ser a superfície de ataques e a probabilidade de ter bugs será menor.


### Cuidado com variáveis de armazenamento {#cuidado-com-variáveis-de-armazenamento}

Tome cuidado ao utilizar variáveis de armazenamento (ou storage variables).

Use-as de forma eficiente e o mínimo possível.


### Deixe on-chain apenas o necessário {#deixe-on-chain-apenas-o-necessário}

Contratos muito complexos são caros de deployar e de executar.

Tente tornar off-chain toda a lógica desnecessária.


### Evite loops e algorítmos indeterminísticos {#evite-loops-e-algorítmos-indeterminísticos}

Essas operações que podem levar tempos indeterminados para executar devem ser evitadas a todo custo.


### Limite as entradas {#limite-as-entradas}

Limite as entradas de funções a apenas entradas que terão comportamentos esperados.


### Tente lidar com todos os casos possíveis {#tente-lidar-com-todos-os-casos-possíveis}

Tente lidar com todos os casos e comportamentos possíveis que seu código poderá ter para que não haja imprevistos.


### Evite estruturas paralelas {#evite-estruturas-paralelas}

Utilizar estruturas paralelas, ou que cuidam ou rastream a mesma coisa, na maioria dos casos, são desnecessárias.

Utilize apenas quando não houver solução melhor.


### Tome muito cuidado com as chamadas externas {#tome-muito-cuidado-com-as-chamadas-externas}

Chamadas externas são os principais locais onde os ataques ocorrem.

Os principais assuntos a ter cuidado com chamadas externas são:


#### Reentrada {#reentrada}

Reentrada é o tipo de ataque mais popular e que acontece em chamadas externas.

Certifique-se de utilizar o padrão CEI (Check-Effect-Interaction) ou o modificador `nonReentrant` da OpenZeppelin.


#### Denial of Service {#denial-of-service}

Denial of Service é o segundo tipo de ataque mais popular e que acontece em chamadas externas.

Certifique-se de que a função de chamada externa não irá falhar.


#### Retorno de valores {#retorno-de-valores}

Cheque todos os valores possíveis e inesperados.


#### Gas {#gas}

Se a chamada de função não for confiável, não encaminhe todo o gas
