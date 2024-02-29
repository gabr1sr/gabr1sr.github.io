+++
title = "Token Standard (ERC-20)"
author = ["Gabriel Rosa"]
date = 2024-01-15T03:48:00-03:00
draft = false
+++

tags
: [Ethereum Request for Comments (ERC)]({{< relref "ethereum_request_for_comments_erc.md" >}})

source
: [Introduction to ERC fundamentals and ERC20 - Updraft Cyfrin](https://updraft.cyfrin.io/courses/advanced-foundry/How-to-create-an-erc20-crypto-currency/erc-and-erc20-fundamentals?lesson_format=video), [ERC-20: Token Standard - EIPs](https://eips.ethereum.org/EIPS/eip-20), [ERC-20 Token Standard - ethereum.org](https://ethereum.org/en/developers/docs/standards/tokens/erc-20)

É o ERC que implementa o padrão de tokens fungíveis para a Ethereum.


## Implementações {#implementações}

-   [Solady](https://github.com/vectorized/solady)
-   [OpenZeppelin](https://github.com/OpenZeppelin/openzeppelin-contracts)
-   [Solmate](https://github.com/transmissions11/solmate)


## Eventos {#eventos}


### Transfer {#transfer}

-   Deve ser emitido quando tokens são transferidos, mesmo que sejam 0 tokens.
-   Quando novos tokens são criados, deve ser emitido com o endereço `from` sendo `0x0`.

`event Transfer(address indexed from, address indexed to, uint256 value)`


### Approval {#approval}

-   Deve ser emitido em qualquer chamada bem-sucedida a `approve(address,uint256)`.

`event Approval(address indexed owner, address indexed spender, uint256 value)`


## Métodos {#métodos}


### name {#name}

-   Retorna o nome do token.

`function name() public view returns (string)`


### symbol {#symbol}

-   Retorna o símbolo do token.

`function symbol() public view returns (string)`


### decimals {#decimals}

-   Retorna o número de decimais que o token usa para representar uma unidade.

`function decimals() public view returns (uint8)`


### totalSupply {#totalsupply}

-   Retorna o supply total do token.

`function totalSupply() public view returns (uint256)`


### balanceOf {#balanceof}

-   Retorna a quantidade de tokens que o endereço `owner` tem.

`function balanceOf(address owner) public view returns (uint256)`


### transfer {#transfer}

-   Transfere `value` de tokens para o endereço `to`.
-   Deve emitir o evento `Transfer`.
-   Deve dar `throw` se quem chamou a função não tiver tokens suficientes.
-   A transferência de valor 0 deve ser tratada normalmente.

`function transfer(address to, uint256 value) public returns (bool)`


### transferFrom {#transferfrom}

-   Transfere `value` de tokens do endereço `from` para o endereço `to`.
-   Deve emitir o evento `Transfer`.
-   Deve dar `throw` ao menos que o endereço `from` tenha deliberadamente autorizado o chamador da função a transferir os tokens.
-   A transferência de valor 0 deve ser tratada normalmente.

`function transferFrom(address from, address to, uint256 value) public returns (bool)`


### approve {#approve}

-   Permite que o endereço `spender` possa sacar até `value` de tokens da sua conta.
-   Se chamada novamente, a função irá sobrescrever o `valor` permitido ao `spender` movimentar.

`function approve(address spender, uint256 value) public returns (bool)`


### allowance {#allowance}

-   Retorna a quantidade de tokens do endereço `owner` que o endereço `spender` pode movimentar.

`function allowance(address owner, address spender) public view returns (uint256)`
