+++
title = "Blocos (Blockchain)"
author = ["Gabriel Rosa"]
date = 2023-11-28T13:06:00-03:00
tags = ["blockchain", "blocks"]
draft = false
+++

tags
: [Blockchain]({{< relref "blockchain.md" >}})

source
: [What even is a blockchain? - LearnWeb3](https://learnweb3.io/lessons/what-even-is-a-blockchain/)

Blocos são estruturas de dados que agrupam transações e dados, que foram verificados e gravados pelos Nodes da rede através de um processo chamado de [Consenso]({{< relref "consenso.md" >}}), para serem incluídos em uma Blockchain.

Cada bloco contém pelo menos 2 hashs criptográficos:

1.  hash para servir de identificação única desse bloco;
2.  hash do bloco anterior, para manter um histórico rastreável.

Além disso, cada bloco representa um estado em que a blockchain está ou já esteve. O primeiro estado (ou bloco) é chamado de [Bloco Gênese (Blockchain)]({{< relref "bloco_genese_blockchain.md" >}}).

É uma lista de transações mineradas juntas.
