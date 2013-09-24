========
Overview
========

vim-scrollback is an extension for urxvt which provides a vim like scrollback
mode and pasting

=====
Usage
=====

While not in vim scrollback mode

- ctrl-v - enter vim-scrollback mode
- ctrl-r * - pastes the primary clipboard onto the command line
- ctrl-r + - pastes the secondary clipboard onto the command line

Note: both ctrl-v and ctrl-r can be configured to different values
as described in the Configuration section below.

While in the vim scrollback mode the following key bindings are available:

- motions:

  - h j k l
  - w e b
  - 0 _ $
  - ctrl-u ctrl-d ctrl-f ctrl-b
  - gg G
  - f<char> - jump to next occurrence of <char> on the current line
  - F<char> - jump to prev occurrence of <char> on the current line

- visual mode:

  - V v ctrl-v
  - gv - reselect last selection

- yank visual selection (requires xclip):

  - y - yank to primary clipboard (*)
  - Y - yank to secondary clipboard (+)

- paste:

  - p - pastes onto the end of the command line

- undo / redo:

  - u / ctrl-R - undo / redo pastes to command line

- marks:

  - m[a-z] '[a-z] ''

- search:

  - / - searches up
  - ? - searches down
  - n - next in current direction
  - N - next in opposite direction
  - \* - search for word under the cursor

- misc:

  - gf - behave like the shipped matcher plugin for urxvt. Allows you to open a
    url or other configured pattern and launcher. See matcher docs for info on
    configuring:
    http://cvs.schmorp.de/rxvt-unicode/doc/rxvtperl.3.html#PREPACKAGED_EXTENSIONS

Note: counts can be supplied to most commands like in vim

============
Installation
============

After cloning the repository to the location of your choice, you must then
enable this extension in urxvt vi your .Xresources file (or ~/.Xdefaults).

::

  ! enable the extension (note that you must use an absolute path, no ~/...)
  urxvt*perl-lib: /home/user/urxvt-vim-scrollback
  urxvt*perl-ext-common: vim-scrollback

=============
Configuration
=============

Vim scrollback supports various configuration settings which can be supplied
in your ~/.Xresources (or ~/.Xdefaults) file.

::

  ; configure alt-s as the keybinding to enter vim scrollback mode.
  urxvt.vim-scrollback: M-s

  ; configure alt-p as the keybinding to paste mode.
  urxvt.vim-scrollback-paste: M-p

  ; configure the background and foreground colors used for the status bar while
  ; in scrollback mode.
  urxvt.vim-scrollback-bg: 16
  urxvt.vim-scrollback-fg: 10

  ; configure vim-scrollback specific matchers
  urxvt.vim-scrollback.pattern.1: \\B(/\\S+?):(\\d+)(?=:|$)
  urxvt.vim-scrollback.launcher.1: gvim +$2 $1

  ; configure the command used when opening urls. Note: uses the same
  ; configuration as the url launcher script shipped with urxvt.
  urxvt*urlLauncher: firefox
