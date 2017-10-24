`nim-mode` A major mode for editing Nim source code[![Travis CI](https://travis-ci.org/nim-lang/nim-mode.svg?branch=master)](https://travis-ci.org/nim-lang/nim-mode)
===================================================

This package provides (requires Emacs 24.4 or higher version):

- Syntax highlight for .nim, .nims, nimble, nim.cfg
- Auto-indent
- Outline by procedures (`hs-hide-all`, `hs-show-all` etc.)
- more features with Nimsuggest: auto-lint, auto-completion, eldoc (hover)

## TL;DR

For regular emacs users, all you need is below configuration in your
dot emacs after you installed nim-mode from MELPA and nimsuggest
which you can make by `./koch tools` or `./koch nimsuggest`command in
the Nim repository (or check the official document on Nim website if
this information was outdated):

``` elisp
(add-hook 'nim-mode-hook 'nimsuggest-mode)

;; Below configs are can be optional
;;
;; The `nimsuggest-path` will be set the value of
;; (executable-find "nimsuggest"), automatically.
(setq nimsuggest-path "path/to/nimsuggest")

;; You may need to install below package if you haven't installed yet.

;; -- Auto completion --
;; You can omit if you configured company-mode on 'prog-mode-hook
(add-hook 'nimsuggest-mode-hook 'company-mode)  ; auto complete package
;; -- Auto lint --
;; You can omit if you configured flycheck-mode on 'prog-mode-hook
(add-hook 'nimsuggest-mode-hook 'flycheck-mode) ; auto linter package
;; If you use Emacs 26 or higher, you can also use `flymake' package which
;; Emacs' builtin standard package for auto lint (it was re written on
;; Emacs 26) which you can use by below config:
;; (add-hook 'nimsuggest-mode-hook 'flymake-mode) ; auto linter package

;; Note that currently nim-mode has three choice for the flyXXX's auto
;; linter and currently nim-mode repo has `flycheck-nimsuggest' and
;; `flymake-nimsuggeset'. On the future plan, this repo will only ship
;; `flymake-nimsuggst' because it is Emacs 26 builtin.

;; FYI:
;; might be supproted in the future, but not for now
;; (add-hook 'nimsuggest-mode-hook 'nimsuggest-mode)

```

## Installation

* Install `nim-mode.el` via [MELPA](https://melpa.org/#/getting-started).
  * Check the MELPA's link and add the package archive if you don't set yet
  * `M-x package-install`
  *  type `nim-mode` and then enter

Please take a look next `Nimsuggest` section if you interested in
editor integration like code-completion, jump-to-definition, or linting.

## Nimsuggest
(if you are impatient, skip until `install nimsuggest` to install it)

Nimsuggest is an editor agnostic tool for Nim and nim-mode provides:

1. Completion feature -- *C-M-i* and *M-TAB* keys and auto-complete feature if
   you install [company-mode](https://github.com/company-mode/company-mode)
2. Asynchronous linting -- nimsuggest take care .nims files as
   configuration file, so it's smarter than *nim check* command (1)
3. Showing info under the cursor in minibuffer -- (1)
4. Jump to definition feature -- *M-.* for go to def and *M-,* for
   back to before the go to def position
5. Show document of current position's identifier -- *C-c C-d*

(1): those are automatically turned on if you turned on `nimsuggest-mode`

### Install nimsuggest

1. Use stable version:
   See [official download instruction](http://nim-lang.org/download.html) at
   "Installation based on generated C code" section.

2. Use latest version:
   This way may or may not work (depending on Nim or nimsuggest's
   state and we can't support all the way), so use above way
   if you prefer stable.
   ```sh
   #  assuming you already installed Nim
   cd /path/to/Nim_repository
   ./koch tools
   ```

## Other convenience packages for editing Nim source code

Those packages are convenience packages and can be installed same way
as nim-mode (M-x list-packages ...)

- [indent-guide](https://github.com/zk-phi/indent-guide): show visible indent levels
- [quickrun](https://github.com/syohex/emacs-quickrun): emacs port of vim's quickrun
- [company-mode](https://github.com/company-mode/company-mode): auto-complete feature
- [ob-nim](https://github.com/Lompik/ob-nim): org-mode integration focused on Nim
- [wgrep](https://github.com/mhayashi1120/Emacs-wgrep): Writable grep buffer and apply the changes to files (maybe convenient for refactor stuff)
- [suggestion-box-el](https://github.com/yuutayamada/suggestion-box-el): show argument info on the cursor

## Other editors/IDEs

You can also find other editor/IDE plugins for
Nim language [here](https://github.com/nim-lang/Nim/wiki/editor-support)
