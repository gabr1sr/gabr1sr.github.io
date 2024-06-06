+++
title = "Foundry e NixOS: Como Configurar"
author = ["Gabriel Rosa"]
description = "Foundry é o conjunto de ferramentas mais rápido, portátil, modular e popular para o desenvolvimento de aplicações para Ethereum e redes compatíveis com a EVM. Neste artigo, iremos aprender a como instalá-lo em nossa distribuição NixOS."
date = 2024-06-06T10:57:00-03:00
lastmod = 2024-06-06T10:57:50-03:00
slug = "foundry-e-nixos-como-configurar"
tags = ["solidity", "foundry", "nixos", "br"]
draft = false
weight = 2001
+++

Foundry é o meu conjunto de ferramentas favorito e também o de muita gente. É utilizado tanto por engenheiros de contratos inteligentes quanto por pesquisadores de segurança e hackers que mexem com Solidity.

É muito conhecido pela diminuição da troca de contexto no desenvolvimento e testes de contratos inteligentes. Enquanto no HardHat você escreve os contratos em Solidity, testes e scripts em JavaScript (ou TypeScript), no Foundry você escreve todos eles utilizando apenas Solidity.

Além disso, podemos criar e executar testes avançados sem precisar de dependências externas. A biblioteca padrão do Foundry (`forge-std`) nos possibilita escrever testes unitários, testes de integração, fuzzing testes e testes de invariantes (propriedades) sem precisar instalar nenhum outro programa ou adicionar pacote.

E podemos fazer verificação formal sem criar código extra utilizando o Halmos. Porém, estes assuntos ficarão para artigos futuros.

O Foundry, sem muitos detalhes, é composto pelos seguintes programas:

-   ****Forge****: ambiente de desenvolvimento e testes para Ethereum (como o Truffle, HardHat e DappTools);
-   ****Cast****: possibilita interagir com contratos inteligentes da EVM, enviar transações e pegar dados diretamente do terminal;
-   ****Anvil****: Ethereum node local, como o Ganache, ou HardHat Node, geralmente utilizada para testar o deploy de contratos inteligentes e forkar outras chains;
-   ****Chisel****: Solidity interativo (REPL).


## Instalação genérica {#instalação-genérica}

Podemos instalar o Foundry da mesma forma que em qualquer distribuição Linux utilizando o [guia de instalação](https://book.getfoundry.sh/getting-started/installation):

```shell
$ curl -L https://foundry.paradigm.xyz | bash
```

Desta forma, ele será instalado no diretório `.foundry` da sua `$HOME` e você poderá utilizar o programa `foundryup` para atualizar o conjunto de ferramentas sempre que quiser.

Porém, este não é o "modo Nix" de instalar os programas.


## Utilizando o Nix {#utilizando-o-nix}

Se você não necessariamente quer instalar, mas utilizar o Foundry em sua distribuição, você pode rodar as aplicações do repositório utilizando o Nix (versão 2.4 ou superior):

```shell
$ nix run github:shazow/foundry.nix # Roda a aplicação padrão `forge`
$ nix run github:shazow/foundry.nix#forge # Roda a aplicação `forge`
$ nix run github:shazow/foundry.nix#cast # Roda a aplicação `cast`
$ nix run github:shazow/foundry.nix#anvil # Roda a aplicação `anvil`
$ nix run github:shazow/foundry.nix#chisel # Roda a aplicação `chisel`
```

Se precisar especificar utilizar alguma flag como, por exemplo, `forge build`, basta passar ela depois do `--`:

```shell
$ nix run github:shazow/foundry.nix#forge -- build
```

Se prefere não passar o repositório toda hora que quiser executar alguma aplicação, basta entrar no shell com os binários do repositório injetados:

```shell
$ nix develop github:shazow/foundry.nix
```

E executar normalmente a aplicação desejada:

```shell
$ forge
```


## Utilizando o Flakes {#utilizando-o-flakes}

Esta é a forma mais útil e que eu recomendo de se instalar o Foundry no NixOS, pois podemos montar um template e carregar o Foundry automaticamente. Utilizaremos o mesmo repositório que na seção anterior: [foundry.nix](https://github.com/shazow/foundry.nix)

O primeiro passo é você já ter o Flakes [ativado](https://nixos.wiki/wiki/Flakes) no seu sistema.

A próxima etapa é criar um `flake.nix` no diretório atual através do seguinte comando:

```shell
$ nix flake init
```

Se você simplesmente criar um arquivo `flake.nix` sem utilizar o comando citado, irá se deparar com erros na hora de entrar no ambiente.

Para a terceira etapa, edite o arquivo `flake.nix`, insira o repositório nas `inputs`, carregue seu overlay e adicione o `foundry-bin` e o `solc` aos `buildInputs` do `devShell`. Ou simplesmente copie o código abaixo:

```nix
{
  description = "Solidity project using Foundry";

  inputs = {
    nixpkgs.url = "github:nixos/nixpkgs/nixpkgs-unstable";
    utils.url = "github:numtide/flake-utils";
    foundry.url = "github:shazow/foundry.nix";
  };

  outputs = { self, nixpkgs, utils, foundry, nur }:
    utils.lib.eachDefaultSystem (system:
      let
        pkgs = import nixpkgs {
          inherit system;
          overlays = [ foundry.overlay nur.overlay ];
        };
      in {
        devShell = pkgs.mkShell {
          buildInputs = [
            pkgs.foundry-bin
            pkgs.solc
          ];

          shellHook = ''
            if [ ! -e ./foundry.toml ]; then
               forge init --force
            fi
          '';
        };
    });
}
```

Repare que eu adicionei algumas linhas extras no `shellHook`:

```nix
shellHook = ''
  if [ ! -e ./foundry.toml ]; then
    forge init --force
  fi
'';
```

O código que está dentro do `shellHook` irá ser executado assim que você entrar no ambiente do projeto atual. A linha `if [ ! -e ./foundry.toml ]; then` é para identificar se no diretório atual não existe um arquivo `foundry.toml`, o `forge init --force` é para inicializar um projeto Forge no diretório atual mesmo se houverem arquivos e a linha `fi` é para fechar o bloco `then` da condição da primeira linha.

Depois de ter salvo o arquivo, basta entrar no ambiente do diretório atual:

```shell
$ nix develop
```

Os programas ficarão disponíveis para o ambiente atual e o projeto Forge irá inicializar automaticamente caso não haja nenhum arquivo `foundry.toml`.

Se você não quiser executar esse comando toda vez e quer que entre no ambiente toda vez que você entrar no diretório, instale o [direnv](https://github.com/nix-community/nix-direnv?tab=readme-ov-file#installation), escreva um arquivo `.envrc`:

```shell
if command -v nix-shell &> /dev/null
then
    use flake .
fi
```

E habilite o direnv no diretório atual:

```shell
$ direnv allow
```

Assim, toda vez que você entrar no diretório atual, o ambiente será carregado automaticamente e você poderá focar em coisas mais importantes.

Se quiser criar um template para reutilizar esse setup toda vez que precisar criar um novo projeto com Foundry, basta ir no diretório da configuração do seu NixOS, criar uma pasta `templates/foundry`, entrar nessa pasta, copiar o `flake.nix` e o `.envrc` que fizemos para lá, voltar para a pasta de configuração do sistema e adicionar as seguintes linhas ao `flake.nix`:

```nix
templates = {
  foundry = {
    description = "Foundry Project";
    path = ./templates/foundry;
  };
};
```

Ficará parecido com a configuração do [meu template](https://github.com/gabr1sr/nixos/blob/3ae13b3fee8717ec7394496a6fc8eab081a31068/flake.nix#L64-L68).
