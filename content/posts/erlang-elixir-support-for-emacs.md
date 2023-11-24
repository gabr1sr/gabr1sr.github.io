+++
title = "Erlang and Elixir support for Emacs"
author = ["Gabriel Rosa"]
date = 2023-10-09T06:56:00-03:00
lastmod = 2023-10-09T06:57:01-03:00
tags = ["emacs", "erlang", "elixir", "lsp"]
categories = ["emacs"]
draft = false
weight = 2002
+++

This is a simple tutorial of how to add Erlang and Elixir support for Emacs.


## Erlang LSP {#erlang-lsp}

First, let's start with the Language Server Protocol for Erlang.

Make sure you have [Erlang](https://github.com/erlang/otp#installation) and [Rebar3](https://rebar3.org/docs/getting-started/#installing-from-the-rebar3-escript) installed, download and compile [erlang_ls](https://github.com/erlang-ls/erlang_ls):

```sh
git clone https://github.com/erlang-ls/erlang_ls
cd erlang_ls
make
```

You can choose if you want to install to the default path `/usr/local/bin`:

```sh
make install
```

Or install to a custom directory using the `PREFIX` environment variable:

```sh
PREFIX=/path/to/dir make install
```

Just make sure the installation path is in your `PATH` environment variable.


## Elixir LSP {#elixir-lsp}

Now, you need [Elixir](https://elixir-lang.org/install.html) installed.

Then download and compile [elixir-ls](https://github.com/elixir-lsp/elixir-ls):

```sh
git clone https://github.com/elixir-lsp/elixir-ls
cd elixir-ls
MIX_ENV=prod mix do deps.get, compile
```

And install to the default path `elixir-ls/release`:

```sh
MIX_ENV=prod mix elixir_ls.release
```

Or to a custom directory:

```sh
MIX_ENV=prod mix elixir_ls.release -o ~/.local/bin
```

Remember: the installation path must be in your `PATH` environment variable.


## Erlang support for Emacs {#erlang-support-for-emacs}

Open your Emacs config file and install the [erlang.el](https://www.erlang.org/doc/man/erlang.el.html) package:

```emacs-lisp
(use-package erlang
  :ensure t
  :hook (erlang-mode . eglot-ensure))
```

Notice we added `:hook (erlang-mode . eglot-ensure)` to use Eglot (LSP client for Emacs, built-in since version 29).

Eglot already use erlang_ls for erlang.el[^fn:1].


## Elixir support for Emacs {#elixir-support-for-emacs}

We are going to use the Emacs 29 built-in Tree-Sitter for Elixir support. If your version is lower than 29, consider using [elixir-mode](https://github.com/elixir-editors/emacs-elixir).

First, we need to tell built-in Tree-Sitter the languages we want to install. So open add these lines to your Emacs config file:

```emacs-lisp
(setq treesit-source-alist
      '((elixir "https://github.com/elixir-lang/tree-sitter-elixir")
        (heex "https://github.com/phoenixframework/tree-sitter-heex")))
```

You can eval this line using the command `C-M-x` or `M-x eval-defun`.

Then, run `M-x treesit-install-language-grammar` and install both `heex` and `elixir` language grammar (you will need a C Compiler and Make).

Now let's config [elixir-ts-mode](https://github.com/wkirschbaum/elixir-ts-mode) and [heex-ts-mode](https://github.com/wkirschbaum/heex-ts-mode):

```emacs-lisp
(use-package elixir-ts-mode
  :ensure t
  :hook (elixir-ts-mode . eglot-ensure))

(use-package heex-ts-mode
  :ensure t
  :hook (heex-ts-mode . eglot-ensure))
```

If you are using Emacs 30+, you can ommit the `:ensure t` of these 2 packages because they are built-in[^fn:2].

And, to complete this post, we can setup the LSP for Elixir using Eglot (you don't need to do this if you are using Emacs 30+):

```emacs-lisp
(add-to-list 'eglot-server-programs
             '((elixir-ts-mode heex-ts-mode) . ("language_server.sh")))
```

For Windows, just use `language_server.bat` instead of `language_server.sh`.

That's it.

[^fn:1]: <https://github.com/emacs-mirror/emacs/blob/c55e22c418048463a83e6b0e29c727c4f7b09545/lisp/progmodes/eglot.el#L264>
[^fn:2]: <https://github.com/emacs-mirror/emacs/blob/63a6fb2a7a02ca88835c3fd473894d3b7d39ff15/etc/NEWS#L859>