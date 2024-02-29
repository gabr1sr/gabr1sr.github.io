+++
title = "Check-Effects-Interactions (CEI)"
author = ["Gabriel Rosa"]
date = 2023-09-12
draft = false
+++

tags
: [Padrões de Segurança (Solidity)]({{< relref "padroes_de_seguranca_solidity.md" >}})

source
: [Check Effects Interactions](https://fravoll.github.io/solidity-patterns/checks_effects_interactions.html), [Use the Checks-Effects-Interactions Pattern](https://docs.soliditylang.org/en/develop/security-considerations.html#use-the-checks-effects-interactions-pattern)

É um padrão criado com o propósito de reduzir a superfície de ataque de contratos inteligentes maliciosos que tentam sequestrar o fluxo de controle após uma chamada externa.


## Metodologia {#metodologia}

-   **Check:** checar se as alterações de estado são possíveis
-   **Effects:** fazer as alterações de estados
-   **Interactions:** executar as funções que interagem com esses estados


## Amostras {#amostras}


### Código Vulnerável {#código-vulnerável}

```solidity
function withdraw(uint256 amount) public {
    require(balances[msg.sender] >= amount, "No sufficient amount");
    (bool success,) = msg.sender.call{value: amount}("");
    require(success, "Failed to withdraw");
    balances[msg.sender] -= amount;
}
```


### Código Usando CEI {#código-usando-cei}

```solidity
function withdraw(uint256 amount) public {
    require(balances[msg.sender] >= amount, "No sufficient amount"); // Check
    balances[msg.sender] -= amount; // Effect
    (bool success,) = msg.sender.call{value: amount}(""); // Interaction
    require(success, "Failed to withdraw");
}
```
