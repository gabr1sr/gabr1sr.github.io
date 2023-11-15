+++
title = "Rust support for Emacs"
author = ["Gabriel Rosa"]
date = 2023-11-15T19:00:00-03:00
lastmod = 2023-11-15T19:02:53-03:00
tags = ["emacs", "rust"]
categories = ["emacs"]
draft = false
weight = 2002
+++

This is a simple tutorial of how to add Rust support for Emacs.


## Rust Analyzer {#rust-analyzer}

First, make sure you have `git`, `rustc` and `cargo` installed on your machine.

Then run these commands in your terminal:

```sh
git clone https://github.com/rust-lang/rust-analyzer -b release
cd rust-analyzer
cargo xtask install --server
```

And make sure `$HOME/.cargo/bin` is in your `$PATH`.


## Tree Sitter {#tree-sitter}

Now, open up your Emacs and add this line to your `init.el`:

```emacs-lisp
(setq treesit-language-source-alist
      '((rust "https://github.com/tree-sitter/tree-sitter-rust")))
```

Save (`C-x C-s`) and evaluate (`C-M-x`) the code we just added.

Execute `M-x treesit-install-language-grammar` in your Emacs, select language `rust` and wait the build process end.


## Rust Tree Sitter Mode {#rust-tree-sitter-mode}

We gonna use `rust-ts-mode` to provide us syntax highlight for Emacs. This package is built-in in Emacs 29+[^fn:1].

Open your `init.el` again and add these lines:

```emacs-lisp
(use-package rust-ts-mode
  :mode "\\.rs\\'"
  :hook (rust-ts-mode . eglot-ensure)
  :init
  (add-to-list 'org-src-lang-modes '("rust" . rust-ts)))
```


## Org Babel and Rust {#org-babel-and-rust}

If you want to add Org Babel support for Rust, you will need the package `ob-rust`.

Happily, MELPA have this package :)

```emacs-lisp
(use-package ob-rust
  :ensure t)
```

You will also want to add `(rust . t)` to `org-babel-do-load-languages` in your `ob` (Org Babel) package:

```emacs-lisp
(use-package ob
  :custom
  (org-babel-do-load-languages 'org-babel-load-languages
			       '((emacs-lisp . t)
				 (rust . t))))
```

[^fn:1]: <https://github.com/emacs-mirror/emacs/blob/e81e625ab895f1bd3c5263f5b66251db0fd38bd6/etc/NEWS.29#L3069>
