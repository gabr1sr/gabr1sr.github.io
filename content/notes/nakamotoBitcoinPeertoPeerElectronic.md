+++
title = "Notas sobre Bitcoin Whitepaper"
author = ["Gabriel Rosa"]
draft = false
+++

## nakamotoBitcoinPeertoPeerElectronic {#nakamotobitcoinpeertopeerelectronic}


### Resumo {#resumo}

Uma versão puramente ponta-a-ponta de dinheiro eletrônico que possibilita os pagamentos serem feitos diretamente de uma parte para outra sem intermediários ou instituições financeiras.


### Problema no Comércio na Internet {#problema-no-comércio-na-internet}

O comércio na internet é inteiramente dependente do modelo de confiança para processar pagaemtnos eletrônicos.

Transação não reversíveis não são realmente possíveis, já que as instituições financeiras não podem evitar mediar as transações.

O custo de mediação aumenta as taxas de transação.

Com a possibilidade de reversão de transação, a necessidade de confiança aumenta.

Todos os custos extras e pagamentos incertos podem ser evitados com pagamentos físicos pessoalmente, porém, não existe nenhum mecanismo online para isso.


### Solução do Problema no Comércio na Internet {#solução-do-problema-no-comércio-na-internet}

O que é necessário para resolver esse problema é um sistema de pagamento eletrônico baseado em provas criptográficas ao invés de confiança, possibilitando que 2 partes possam fazer transações diretas sem precisar confiar em terceiros.

Transações que são computacionalmente inviáveis de reverter protege os vendedores da fraude, enquanto mecanismos de garantia podem ser implementados para proteger os compradores.


### Transações {#transações}

Nós podemos dizer que moedas eletrônicas são uma cadeia de assinaturas digitais.

Cada dono transfere a moeda para o outro assinando digitalmente o hash da transação anterior e a chave pública do próximo dono e adicionando estes ao final da moeda.


### Problema da Verificação do Double-Spending {#problema-da-verificação-do-double-spending}

O problema é que o beneficiário não pode verificar se os donos não estão gastando duas vezes a moeda (double-spending).

Para conseguir evitar o double-spending sem precisar de terceiros, as transações devem ser todas públicas e transparentes, além de precisar de um sistema para os participantes concordarem com um único histórico na ordem em que são recebidos.

O beneficiário precisa da prova que ao tempo de cada transação, a maioria dos nós concordaram que isso foi recebido primeiro.


### Solução para o Problema da Verificação do Double-Spending {#solução-para-o-problema-da-verificação-do-double-spending}

A solução proposta para esse problema começa com a implementação de um servidor baseado em marcações de tempo (timestamp).

Um servidor baseado em marcações de tempo funciona pegando o hash de um bloco de itens que serão marcados com um tempo e publicando o hash.

A marcação de tempo prova que os dados devem ter existido no tempo específico para terem sido transformados em hash.

Cada marcação de tempo inclui a marcação de tempo do bloco anterior em seu hash, formando uma cadeia, com cada marcação de tempo adicional reforçando o anterior.


### Provas-de-Trabalho (Proof-of-Work) {#provas-de-trabalho--proof-of-work}

Para implementar o servidor de marcações de tempo em uma base ponta-a-ponta, precisamos utilizar um sistema de prova-de-trabalho similar ao do Hashcash ao invés de um sistema de postagem de jornal.

A prova-de-trabalho envolve procurar por um valor que quando feito hash, com SHA-256, por exemplo, o hash comece com um número específico de 0 bits.

A média do trabalho requerido é exponencial ao número de 0 bits necessários e pode ser verificado executando um único hash.


### Provas-de-Trabalho em uma Rede de Marcações de Tempo {#provas-de-trabalho-em-uma-rede-de-marcações-de-tempo}

Para a nossa rede de marcações de tempo, nós implementados as provas-de-trabalho incrementando o nonce do bloco até que o valor encontrado faça com que o hash do bloco tenha a quantidade necessária de 0 bits.

Uma vez que o esforço da CPU foi usado para solucionar essa prova-de-trabalho, o bloco não pode ser mudado sem que o trabalho seja refeito.

Conforme mais blocos são adicionados depois, o trabalho para mudar o bloco inclui refazer todos os blocos depois deste.

A prova-de-trabalho também resolve o problema de determinar a representação na tomada de decisão da maioria.

Se a maioria for baseado em 1 endereço IP = 1 voto, isso pode ser manipulado por qualquer um que consiga alocar vários IPs.

A prova-de-trabalho é essencialmente 1 CPU = 1 voto.

A decisão da maioria é representado pela cadeia mais longa (longest chain), que é o maior esforço que a prova-de-trabalho investe.

Se a maioria do poder de CPU é controlado por nós honestos, a cadeia honesta vai crescer rapidamente e ultrapassar as cadeias concorrentes.

Para modificar um bloco antigo, um atacante teria que refazer a prova-de-trabalho do bloco e todos os blocos depois deste e então alcançar e superar o trabalho dos nós honestos.

Para compensar a velocidade crescente de hardware e interesse variável na execução de nós ao longo do tempo, a dificuldade da prova-de-trabalho é determinada por uma média móvel visando um número médio de blocos por hora.

Se forem gerados muito rápido, a dificuldade aumenta.


### Passo a Passo de Como a Rede Funciona {#passo-a-passo-de-como-a-rede-funciona}

A rede funciona da seguinte forma:

1.  Novas transações são transmitidas para todos os nós.
2.  Cada nó agrupa novas transações dentro de um bloco.
3.  Cada nó trabalha em encontrar a prova-de-trabalho para esse bloco.
4.  Quando um nó acha a prova-de-trabalho, ele transmite o bloco para todos os nós.
5.  Os nós aceitam o bloco apenas se todas as transações nele são válidas e se ainda não foram gastas.
6.  Os nós dizem que aceitaram o bloco trabalhando na criação do próximo bloco na cadeia, usando o hash do bloco aceito como hash anterior.

Os nós sempre consideram a maior cadeia como sendo a correta e vão continuar a extendê-la.

Se 2 nós transmitem diferentes versões do próximo bloco de forma simultânea, alguns nós podem receber uma ou outra primeiro.

Nesse caso, eles trabalham usando o primeiro bloco que receberam, mas salvam a outra cadeia para o caso dela se tornar maior.

Essa disputa acaba quando a próxima prova-de-trabalho é encontrada e uma das cadeias se torna a maior. Desta forma, os nós que estavam trabalhando na outra cadeia vão mudar para a cadeia maior.

Novas transações não precisam necessariamente chegar a todos os nós. Com o tanto que eles cheguem a alguns nós, eles podem fazer parte de algum bloco.

Transmissões de blocos também são tolerantes à quedas de mensagem.

Se um nó não receber um bloco, ele pode requisitar este bloco quando receber o próximo bloco (momento em que percebe que se esqueceu de um bloco).


### Incentivo {#incentivo}

A primeira transação de um bloco é uma transação especial que cria novas moedas pertencentes ao criador do bloco atual.

Isso funciona como método de incentivo para os nós continuarem ajudando a rede.

Além disso, funciona como uma forma de começar a distribuir moedas que entrarão em circulação, já que não tem uma autoridade central emitindo elas.

Esse incentivo também pode ser providenciado usando taxas de transações.

Se o valor de saída de uma transação é menor que seu valor de entrada, a diferença é a taxa de transação que é adicionada ao valor de incentivo do bloco que contém a transação.

Assim que um predeterminado número de moedas estiverem entrado em circulação, o incentivo pode ser feito inteiramente por apenas taxas de transações, se tornando completamente livre de inflação.

O incentivo pode ajudar a encorajar os nós a serem honestos.


### Espaço em Disco {#espaço-em-disco}

Uma vez que a última moeda em uma transação for gravada em blocos suficientes, as transações de gasto anteriores podem ser descartadas para economizar espaço em disco.

Para facilitar isso sem quebrar o hash do bloco, as transações são "hasheadas" em uma Merkle Tree, com apenas a raíz incluída no hash do bloco.

O cabeçalho de um bloco sem transações ocuparia cerca de 80 bytes.

Se supormos que blocos são gerados a cada 10 minutos, 80 bytes \* 6 \* 24 \* 365 = 4.2 MB por ano.


### Verificação de Pagamento Simplificado {#verificação-de-pagamento-simplificado}

É possível verificar pagamentos sem precisar de um nó inteiro.

Um usuário só precisa manter uma cópia dos cabeçalhos de blocos da cadeia mais longa e obter o "galho" em que a transação está na Merkle Tree.

O usuário não pode checar a transação por si mesmo, mas pode saber se um nó a aceitou e os blocos adicionados depois dele confirmam se a rede a aceitou ou não.


### Proteção Contra Fraude {#proteção-contra-fraude}

Com o tanto que os nós honestos componham a maior parte da rede, os dados gravados na blockchain são confiáveis.

Enquanto os nós da rede podem verificar as transações por eles mesmos, o método simplificado de verificação pode ser fraudado com o tanto que o atacante controle maior parte do poder da rede.

Uma estratégia para impedir que essa fraude ocorra é aceitar alertas de nós da rede que detectaram algum bloco inválido, fazendo com que o software do usuário baixe o bloco inteiro e as transações alertadas para confirmar a inconsistência.


### Combinando e Dividindo Valores em uma Transação {#combinando-e-dividindo-valores-em-uma-transação}

As transações podem conter múltiplas entradas e saídas, possibilitando combinar e dividir valores.


### Privacidade {#privacidade}

Apesar de todas as transações serem públicas, a privacidade ainda pode ser mantida se as chaves públicas forem anônimas. Ou seja, a cada transação podemos utilizar chaves públicas diferentes para manter em sigilo nossa identidade.
