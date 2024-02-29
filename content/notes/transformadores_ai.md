+++
title = "Transformadores (AI)"
author = ["Gabriel Rosa"]
date = 2023-11-28T12:47:00-03:00
tags = ["ai", "ml", "nn", "nlp", "transformers"]
draft = false
+++

tags
: [Redes Neurais (NN)]({{< relref "redes_neurais_nn.md" >}}), [Processamento de Linguagem Natural (NLP)]({{< relref "processamento_de_linguagem_natural_nlp.md" >}})

source
: [Intro to Large Language Models (LLMs)](https://learnweb3.io/degrees/ai-developer-degree/freshman-ai/intro-to-large-language-models-llms/)

Transformadores são um tipo de arquitetura de Redes Neurais que revolucionou o campo de Processamento de Linguagem Natural (NLP).

Eles são projetados para processar dados sequenciais, como sentenças ou texto, capturando as relações entre as palavras ou tokens.

Diferente das redes neurais recorrentes, que processam dados de entrada de forma sequencial, os transformadores podem processar a sequência inteira em paralelo.

Isso significa que eles não precisam ler palavra por palavra. Eles podem ler a frase inteira de uma vez.

Isso os torna mais rápidos e os ajuda a entender como palavras diferentes na frase se encaixam.

Esse processamento paralelo se torna possível graças aos mecanismos que chamamos de self-attetion e attention.

Uma das principais vantagens dos transformadores é a seu longo-alcance em detectar dependências nos dados de entrada, o que é crucial para entender o contexto das palavras ou tokens em linguagem natural.

Isso os faz altamente efetivos em tarefas como tradução de linguagens, análise de sentimentos, geração de texto e muitas mais.


## Self-attention {#self-attention}

Mecanismo que possibilita os transformadores pesarem a importância de diferentes palavras ou tokens dentro de uma frase baseado em suas relevâncias umas para as outras.

Ele calcula esses pesos considerando a relação entre todos os pares de palavras na sequência de forma simultânea.


## Attention {#attention}

Esse mecanismo, por outro lado, possibilita aos transformadores focarem em partes específicas da sequência de entradas enquanto processa os dados.

Isso possibilita ao modelo atribuir maior importância para certas palavras ou tokens que são mais relevantes para a tarefa atual.
