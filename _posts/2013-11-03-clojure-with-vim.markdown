---
layout: post
title: Clojure with Vim
date: 2013-11-03 13:42
comments: true
categories: software clojure vim
---
These notes are intended to be used alongside [this screencast](http://youtu.be/LiA56W3V3_w), and describe some aspects of setting up and using a clojure editing environment in vim, if for some reason you don't want to use emacs. It is very unlikely that I would ever switch to emacs, but if there is a killer feature of emacs/clojure not found here that you cannot live without, I'd be interested in knowing about it, so that I can cry myself to sleep/try to figure out if anyone in the [clojure/vim community](https://groups.google.com/forum/#!forum/vimclojure) (not just for the VimClojure plugin any more) has replicated the functionality.

Assuming you don't want to clone [my dotfiles repo](https://github.com/burnettk/dotfiles), which are pretty much [skwp's dotfiles](https://github.com/skwp/dotfiles) but with some extra clojure stuff, here's the important parts for clojure:

## Install

* Follow the [vim-fireplace](https://github.com/tpope/vim-fireplace) installation instructions.

* Install [Rainbow-Parentheses-Improved-and2](https://github.com/vim-scripts/Rainbow-Parentheses-Improved-and2) and add the following two lines to your vim configs:

```
let g:rainbow_active = 1
let g:rainbow_operators = 1
```

* Make sure your Clojure project follows [leiningen](http://leiningen.org/) conventions, possibly by generating your project with leiningen:

```
lein new todos
```

## Using this setup

In a terminal window, start up a lein repl:

```
cd todos
lein repl
```

In a second terminal window, open up your project in vim.

There's lots of ways to open the file you want to edit in vim. I like using [ctrlp](https://github.com/kien/ctrlp.vim), which has nothing to do with clojure.

My clojure source files have sweet syntax highlighting and indentation from [vim-clojure-static](https://github.com/guns/vim-clojure-static), but pretty much all of the functionality comes from [vim-fireplace](https://github.com/tpope/vim-fireplace).

These are the features from fireplace I use a lot (borrowing heavily from tpope's docs here):

* `cpp` to evaluate the expression under the cursor

* `K` to look up the docs for the symbol under the cursor

* `[d` to look up the source code for the symbol under the cursor

* `gf` to "go to the file" corresponding to the namespace under the cursor

* `Require!` to require the current namespace with `:reload-all`, which also reloads dependencies

* `:help fireplace` for the rest

There's lots of other info out there regarding using vim to write clojure, including [vim docs on clojure's site itself](http://dev.clojure.org/display/doc/Getting+Started+with+Vim).
