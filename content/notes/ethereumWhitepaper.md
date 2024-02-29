+++
title = "Ethereum Foundation - Ethereum Whitepaper"
author = ["Gabriel Rosa"]
draft = false
+++

## Anotações de Leitura {#anotações-de-leitura}


### Intenção {#intenção}

A ideia da Ethereum é fornecer uma blockchain com uma linguagem de programação integrada completa que pode ser utilizada para criar "contratos" (ou contratos inteligentes, ou código que implementa regras arbitrárias) que podem ser utilizados para codificar funções arbitrárias de transição de estado, permitindo que os usuários criem diversos sistemas simplesmente escrevendo a lógica em algumas linhas de código.


### Sobre o Bitcoin {#sobre-o-bitcoin}


#### História {#história}

Entre 1980 e 1990 surge o protocolo anônimo e-cash, que utilizava um primitivo criptográfico chamado de Chuamian blinding e também forneciam uma moeda de alto nível de privacidade, porém ainda havia dependência de um intermediário centralizado.

Em 1998, o WeiDai criou o b-money, que foi a primeira proposta que sugeriu a ideia de criar dinheiro usando a resolução de quebra-cabeças computacionais e consenso descentralizado, porém faltavam detalhes de como o consenso descentralizado poderia ser implementado.

Em 2005, Hal Finney introduziu um conceito de Provas de Trabalho Reutilizáveis, um sistema que usa ideias do b-money junto com quebra-cabeças de Hashcash do Adam Back para criar um conceito de criptomoeda, porém ainda dependia do modelo de confiança como backend.

Em 2009, Satoshi Nakamoto implementou a moeda descentralizada chamada Bitcoin, que combinou os primitivos estabelecidos para gerenciar a propriedade usando criptografia de chave pública e um algoritmo de consenso chamado prova de trabalho.

O mecanismo de prova de trabalho foi uma avanço porque resolveu dois problemas de uma vez só:

1.  Forneceu um algoritmo simples e moderadamente eficaz para que os nós concordassem coletivamente com um conjunto de atualizações canônicas para o estado do livro-razão do Bitcoin.

2.  Forneceu um mecanismo que prevenia ataques cibernéticos e permitia a livre entrada no processo de consenso, resolvendo o problema político de decidir quem o influencia.


#### <span class="org-todo todo TODO">TODO</span> Sistema de transição de estados {#sistema-de-transição-de-estados}
