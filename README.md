[![Build Status](https://github.com/dwcoates/uci-mode/workflows/CI/badge.svg)](https://github.com/dwcoates/uci-mode/actions)

# Overview

An Emacs major-mode for chess engine interaction.

 * [Quickstart](#quickstart)
 * [uci-mode](#uci-mode)
 * [Interactive Commands](#interactive-commands)
 * [Screenshot](#screenshot)
 * [Remote Engines](#remote-engines)
 * [Compatibility and Requirements](#compatibility-and-requirements)

## Quickstart

```bash
$ which stockfish
/usr/local/bin/stockfish
```

```elisp
(require 'uci-mode)
```

<kbd>M-x</kbd> uci-mode-run-engine

## uci-mode

Uci-mode is a comint-derived major-mode for interacting directly with
a UCI chess engine.  Direct UCI interaction is interesting for
programmers who are developing chess engines, or advanced players who
are doing deep analysis on games.  This mode is not useful for simply
playing chess.

Provides

 * syntax highlighting of UCI engine output
 * customizable faces
 * persistent history of UCI commands
 * integration with [pygn-mode](https://github.com/dwcoates/pygn-mode) for PGN editing
 * remote engine access over SSH

## Interactive Commands

No keys are bound by default.  Consider binding keys in an `eval-after-load`
form.

### Engine Commands

 * `uci-mode-run-engine` — Run an inferior UCI engine process
 * `uci-mode-restart-engine` — Restart or replace an inferior UCI engine process
 * `uci-mode-send-stop` — Send a "stop" message to the UCI engine
 * `uci-mode-send-setoptions` — Send the preconfigured value of `uci-mode-engine-setoptions` to the UCI engine

## Screenshot

Showing [pygn-mode](https://github.com/dwcoates/pygn-mode) integration:

<a href="https://github.com/dwcoates/pygn-mode/blob/master/doc/images/gallery.md#uci-mode-integration">
    <img src="https://raw.githubusercontent.com/dwcoates/pygn-mode/master/doc/images/pygn-uci-triple-pane-small.png" width=300/>
</a>

## Remote Engines

The variable `uci-mode-engine-command` accepts a list, the first of which is
the local executable, the remainder of which are arguments.  Assuming that
there is no interactive password prompt, a remote engine may be accessed over
SSH like this:

```elisp
(setq uci-mode-engine-command '("ssh" "example.com" "/usr/local/bin/stockfish"))
```

The value of `uci-mode-engine-command` may also be set via customize.

## Compatibility and Requirements

GNU Emacs 25.1 or higher

A command-line UCI engine executable, the default being [Stockfish](https://stockfishchess.org/)
