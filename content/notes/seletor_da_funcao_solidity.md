+++
title = "Seletor da Função (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-07
draft = false
+++

tags
: [Representação de Funções (Solidity)]({{< relref "representacao_de_funcoes_solidity.md" >}})

source
:

O seletor da função é os primeiros 4 bytes do hash `keccak256` do nome da função juntamento com o tipo de seus argumentos.

Se sua função é `putValue(uint256 value)`, você vai codificar como `putValue(uint256)` usando `keccak256` e pegar os 4 primeiros bytes do resultado.
