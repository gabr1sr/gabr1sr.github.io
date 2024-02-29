+++
title = "Como Funciona o GPT"
author = ["Gabriel Rosa"]
date = 2023-11-28T12:50:00-03:00
tags = ["ai", "ml", "nn", "dl", "transformers", "gpt"]
draft = false
+++

tags
: [Deep Learning (DL)]({{< relref "deep_learning_dl.md" >}}), [Transformadores (AI)]({{< relref "transformadores_ai.md" >}})

source
: [Intro to Large Language Models (LLMs)](https://learnweb3.io/degrees/ai-developer-degree/freshman-ai/intro-to-large-language-models-llms/)

GPT 3, 3.5 e 4 utilizam um modelo de Deep Learning que tem uma arquitetura de Transformador para entender e gerar texto humano. Ele é especificamente projetado para processar tarefas em linguagem natural.


## Como funciona {#como-funciona}

1.  ****pré-treinamento****:
    -   o GPT aprende usando uma grande quantidade de dados de texto, tipicamente retirados da internet.
    -   O modelo prevê a próxima palavra em uma frase a partir da palavra anterior.
    -   Esse processo ajuda o modelo a aprender os padrões estatísticos e relações do texto.

2.  ****arquitetura de transformadores****:
    -   Essa arquitetura ajuda o GPT a entender melhor o contexto e as relações entre as palavras de uma frase.
    -   Os transformadores vão usar o mecanismo de attention para focar em palavras importantes e considerar as relações entre eles.

3.  ****fine-tuning****:
    -   Depois do pré-treinamento, o GPT passa pelo processo de afinação, onde ele melhora em tarefas específicas para se tornar mais aplicável e utilizável.
    -   Esse processo envolve treinar o modelo em um conjunto mais específico com exemplos rotulados.
    -   Ele pode ser afinado, por exemplo, para tarefas como complementar texto, criar resumos ou responder questões.

4.  ****geração****:
    -   Uma vez que o modelo é treinado e afinado, ele pode gerar texto baseado em um determinado prompt ou entrada.
    -   Ele usa seu conhecimento em padrões estatísticos e relações que aprendeu durante o pré-treinamento para gerar texto coerente e contextualmente relevante.
