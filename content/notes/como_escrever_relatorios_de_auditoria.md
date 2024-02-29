+++
title = "Como Escrever Relatórios de Auditoria"
author = ["Gabriel Rosa"]
date = 2023-11-21T07:48:00-03:00
draft = false
+++

tags
: [Auditoria]({{< relref "auditoria.md" >}})

source
: [How To Write A Stellar Finding Report (YT)](https://www.youtube.com/watch?v=DRZogmD647U&t=19766s), [How to Evaluate a Finding Severity (CodeHawks)](https://docs.codehawks.com/hawks-auditors/how-to-evaluate-a-finding-severity)


## Por que é importante escrever bons relatórios? {#por-que-é-importante-escrever-bons-relatórios}

-   Para ganhar os juízes que irão avaliar os relatórios na competição
-   Para ser o relatório selecionado
-   Convencer o protocolo a ser arrumado


## Componentes de um bom relatório {#componentes-de-um-bom-relatório}

-   Causa-raíz clara
-   Impacto claro
-   Curto e bem-explicado (sucinto)
-   Ônus de prova (de preferência Proof of Concept)


## Severidade {#severidade}

Podemos determinar a severidade a partir de 2 pontos: probabilidade e impacto.

| Probabilidade | Impacto | Severidade    |
|---------------|---------|---------------|
| Alta          | Alto    | Alta          |
| Alta          | Médio   | Alta / Média  |
| Alta          | Baixo   | Média         |
| Média         | Alto    | Alta / Média  |
| Média         | Médio   | Média         |
| Média         | Baixo   | Média / Baixa |
| Baixa         | Alto    | Média         |
| Baixa         | Médio   | Média / Baixa |
| Baixa         | Baixo   | Baixa         |


## Dicas {#dicas}

-   Título: &lt;causa-raíz&gt; + &lt;impacto&gt;
