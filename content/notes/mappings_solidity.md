+++
title = "Mappings (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-06
draft = false
+++

tags
: [Tipos Definidos pelo Usuário (Solidity)]({{< relref "tipos_definidos_pelo_usuario_solidity.md" >}})

source
: [Digging deeper into Solidity's syntax](https://learnweb3.io/degrees/ethereum-developer-degree/sophomore/digging-deeper-into-soliditys-syntax/#mappings)

Mappings agem como se fossem hashmaps ou dicionários e são utilizados para guardar informações em pares de chave-valor (key-value).

Podem ser criados com a síntaxe `mapping(keyType => valueType)` e suas chaves e valores podem receber nomes `mapping(keyType keyName => valueType valueName)`.

<a id="code-snippet--MappingExample"></a>
```solidity
contract Mapping {
  mapping(address => uint256) public myMap;

  function get(address _address) public view returns (uint256) {
      return myMap[_address];
  }

  function set(address _address, uint256 value) public {
      myMap[_address] = value;
  }

  function remove(address _address) public {
      delete myMap[_address];
  }
}
```

Nós podemos também criar nested mappings onde a `key` aponta para um segundo nested mapping. Para fazer isso, nós definimos o `valueType` como um mapping:

<a id="code-snippet--NestedMappingExample"></a>
```solidity
contract NestedMappings {
    mapping(address => mapping(uint256 => bool)) public nestedMap;

    function get(address _address, uint256 _number) public view returns (bool) {
        return nestedMap[_address][_number];
    }

    function set(address _address, uint256 _number, bool value) public {
        nestedMap[_address][_number] = value;
    }

    function remove(address _address, uint256 _number) public {
        delete nestedMap[_address][_number];
    }
}
```
