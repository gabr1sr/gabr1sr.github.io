+++
title = "Delegação de Chamada (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-07
draft = false
+++

tags
: [Solidity]({{< relref "solidity.md" >}})

source
: [Run code from other contracts inside your own using delegatecall](https://learnweb3.io/degrees/ethereum-developer-degree/senior/run-code-from-other-contracts-inside-your-own-using-delegatecall/)

É um método utilizado na Solidity para chamar uma função de um contrato específico a partir de um outro contrato. Quando a função é executada em um contrato específico usando `delegatecall()`, o contexto do contrato original é passado para esse contrato específico (i.e., o código é executado no contrato específico, porém, as variáveis são modificadas no contrato original).

```solidity
contract Student {
    uint256 public mySum;
    address public studentAddress;

    function addTwoNumbers(address calculator, uint256 a, uint256 b) public returns (uint256) {
        (bool success, bytes memory result) = calculator.delegatecall(abi.encodeWithSignature("add(uint256,uint256)", a, b));
        require(success, "The call to calculator contract failed");
        return abi.decode(result, (uint256));
    }
}

contract Calculator {
    uint256 public result;
    address public user;

    function add(uint256 a, uint256 b) public returns (uint256) {
        result = a + b;
        user = msg.sender;
        return result;
    }
}
```

No exemplo acima, a variável `mySum` receberá o valor `a + b` e a variável `studentAddress` receberá o valor `msg.sender`. Dentro do contrato `Calculator`, o `result` está no slot0 e o `user` está no slot1. E dentro do contrato `Student`, as variáveis `mySum` e `studentAddress` estão nos mesmos slots. Como a chamada da função `add(uint256,uint256)` foi feita usando `delegatecall`, as variáveis de estado alteradas nos respectivos slots são as do contrato original, que chamou a função `delegatecall` do outro contrato, e não do contrato chamado.
