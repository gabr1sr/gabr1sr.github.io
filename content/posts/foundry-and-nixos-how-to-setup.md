+++
title = "Foundry and NixOS: How To Setup"
author = ["Gabriel Rosa"]
description = "Foundry is a blazing fast, portable, modular and the most popular toolkit for Ethereum and EVM-compĺiant applications development. In this post, we will learn how to install it in our NixOS."
date = 2024-06-06T10:57:00-03:00
lastmod = 2024-06-10T18:19:32-03:00
slug = "foundry-and-nixos-how-to-setup"
tags = ["solidity", "foundry", "nixos", "en"]
draft = false
weight = 2002
+++

Foundry is my favorite toolkit and a lot of people's too. It is used by smart contract engineers, security researchers and hackers who deal with Solidity code.

Is famous for their low context switching environment for smart contract development and testing. While in HardHat you write contracts using Solidity, tests and scripts using JavaScript (or TypeScript), in Foundry we write everything using Solidity only.

Furthermore, we can create and execute advanced tests without needing external dependencies. The Foundry standard library (`forge-std`) allows us to write unit tests, integration tests, fuzzing tests and invariant (property) tests without needing another program or package.

We can also do formal verification with no extra coding using Halmos, but I'll not cover that in this post.

Foundry is composed by these programs:

-   ****Forge****: tests and development environment for Ethereum (like Truffle, HardHat and DappTools);
-   ****Cast****: allows us to interact with EVM smart contracts, send transactions and get chain data;
-   ****Anvil****: local Ethereum node like Ganache or HardHat Node;
-   ****Chisel****: Solidity REPL.


## Generic installation {#generic-installation}

We can install Foundry the same way as in any Linux distro following the [installation guide](https://book.getfoundry.sh/getting-started/installation):

```shell
$ curl -L https://foundry.paradigm.xyz | bash
```

This way it will be installed inside the `.foundry` directory of your `$HOME` and you'll be able to use `foundryup` to update Foundry whenever you want, but this is not the "Nix way" to install programs.


## Using Nix {#using-nix}

If you want to use Foundry in your distro, but not necessarily want to install it, you can run apps from the toolkit using Nix (version 2.4 and superior):

```shell
$ nix run github:shazow/foundry.nix # Runs the default app `forge`
$ nix run github:shazow/foundry.nix#forge # Runs `forge` app
$ nix run github:shazow/foundry.nix#cast # Runs `cast` app
$ nix run github:shazow/foundry.nix#anvil # Runs `anvil` app
$ nix run github:shazow/foundry.nix#chisel # Runs `chisel` app
```

When needing to specify a flag like `forge build` just specify it after `--`:

```shell
$ nix run github:shazow/foundry.nix#forge -- build
```

If you don't want to specify the repo everytime you run a Foundry application, just enter the shell with injected repo binaries:

```shell
$ nix develop github:shazow/foundry.nix
```

And execute the desired application:

```shell
$ forge
```


## Using Flakes {#using-flakes}

This is the way I recommend to install Foundry in your NixOS. You can make a template and load Foundry automatically. We'll use the same repo as before: [foundry.nix](https://github.com/shazow/foundry.nix)

The first step is having Flakes already [enabled](https://nixos.wiki/wiki/Flakes) in your system.

The next step is creating a `flake.nix` file in the current directory through this command:

```shell
$ nix flake init
```

If you simply create the `flake.nix` file without using the command above, you'll face some errors when trying to get into the environment.

Now the third step: edit the `flake.nix` file, add the repo inside the `inputs`, add the repo overlay to the `pkgs` `overlays`, and add `foundry-bin` and `solc` to the `buildInputs` of `devShell`. Or simply copy the following code:

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

Notice that i added some extra code to `shellHook`:

```nix
shellHook = ''
  if [ ! -e ./foundry.toml ]; then
    forge init --force
  fi
'';
```

The `if [ ! -e ./foundry.toml]; then` line identifies if there is a file named `foundry.toml` in the current dir, `forge init --force` will init a new Foundry project in the current dir, and `fi` will close the `then` block.

After saving the file, get into the current dir environment:

```shell
$ nix develop
```

The Foundry apps will be available inside the current environment and the Forge project will automatically init if no `foundry.toml` file exists.

If you don't want to execute this command everytime, install [direnv](https://github.com/nix-community/nix-direnv?tab=readme-ov-file#installation) and create a `.envrc` file:

```shell
if command -v nix-shell &> /dev/null
then
    use flake .
fi
```

Then allow direnv in the current dir:

```shell
$ direnv allow
```

Whenever you `cd` into the current dir the environment will be automatically enabled.

If you want to reuse this setup everytime you need a new Forge project, go to your NixOS config directory, create a `templates/foundry` directory, `cd` into it, copy `flake.nix` and `.envrc` to this directory, get back into the system configuration directory and add the following lines to your `flake.nix`:

```nix
templates = {
  foundry = {
    description = "Foundry Project";
    path = ./templates/foundry;
  };
};
```

It will looks like [my template config](https://github.com/gabr1sr/nixos/blob/3ae13b3fee8717ec7394496a6fc8eab081a31068/flake.nix#L64-L68).


## Using devenv {#using-devenv}

This is the simplest way to install Foundry in your NixOS. First, you need [devenv](https://devenv.sh/) installed in your machine.

Then initialize the devenv in the project directory and add foundry.nix to the inputs of `devenv.yaml` file:

```shell
$ devenv init
$ devenv inputs add foundry github:shazow/foundry.nix --follows nixpkgs
```

And edit the `devenv.nix` file:

```nix
{ ... }:

{
  languages.solidity.enable = true;
  languages.solidity.foundry.enable = true;
}
```

And run `devenv shell` to enter a shell with foundry binaries present.

You can run `direnv allow` to automatically enter this shell whenever you cd into this directory.
