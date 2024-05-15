+++
title = "Emacs syntax checking with Flycheck"
author = ["Dmitry Markushevich"]
date = 2024-05-15
lastmod = 2024-05-15T09:19:55-07:00
tags = ["seedling", "emacs"]
draft = false
+++

[Flycheck](https://www.flycheck.org/) is a syntax checker for Emacs. Confusingly there's another syntax checker called Flymake that is built into Emacs. Flycheck seems to have vastly more functionality though.

Essentially what Flycheck does is shows you "errors" for the buffer that you're editing. Errors are context dependent. In a Ruby file it might be a syntax error. In a blog post, it might be a syntax error.

{{< figure src="/ox-hugo/2024-05-15_08-50-46_screenshot.png" >}}

There's a comparison table between Flycheck and Flymake [here](https://www.flycheck.org/en/latest/user/flycheck-versus-flymake.html#supported-languages).


## Installation {#installation}

There are whole bunch of modules you can install with flycheck, but you need the base package first:

```elisp
(use-package flycheck
:ensure t
:config
(add-hook 'after-init-hook #'global-flycheck-mode))
```


### Language-tool {#language-tool}

I initially looked into flycheck because I was interested in using [languagetool](https://languagetool.org); a spelling and grammar checker on steroids.

flycheck-languagetool requires an external binary (see the `flycheck-languagetool-server-jar` below).

```elisp
(use-package flycheck-languagetool
  :ensure t
  :hook (text-mode . flycheck-languagetool-setup)
  :init
  (setq flycheck-languagetool-server-jar "/opt/homebrew/Cellar/languagetool/6.4/libexec/languagetool-server.jar"))
```


## Usage {#usage}

1.  Enable `global-flycheck-mode`
2.  Install language appropriate packages.
3.  In the case of on languagetool, you can enable grammar and syntax checks in current buffer by executing `M-x flycheck-languagetool-setup`.
4.  Flycheck will do its thing, usually by underlining suspected errors. A buffer with a full listing of issues can be popped up with `M-x flycheck-list-errors`.


## Limitations {#limitations}

Flycheck is useful for identifying errors. It cannot fix issues or offer recommendations on how to fix issues.
