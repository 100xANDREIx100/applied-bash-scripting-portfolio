# ⌨️ Vim Mastery Cheat Sheet

This document tracks my progress learning `vim`, the ubiquitous terminal text editor.

## ⚙️ Installation & Setup
| Command / Concept | Description |
| :--- | :--- |
| `sudo apt install vim` | Installs vim. |
| `vim` or `vi` | Run these to check if vim is installed. |
| `.vimrc` | The configuration file where you can save your vim settings permanently. |
| `.ideavimrc` | The configuration file for JetBrains IDEs when using the IdeaVim plugin. |
| **Neovim (`nvim`)** | A highly customizable alternative. Its commands can also be used in other IDEs. |

## 📁 Opening Files (Terminal)
| Command | Description |
| :--- | :--- |
| `vim 'file'` | Opens a file with vim. If the file does not exist, it will create it. |
| `vi 'file'` | Opens a file with vi. |
| `nvim 'file'` | Opens a file with neovim. |

## 🔄 Core Modes
| Mode | Key(s) to Enter | Description |
| :--- | :--- | :--- |
| **Normal** | `ESC` | Default mode for navigation, deletion, and copying. |
| **Insert** | `i`, `I`, `a`, `A`, `o`, `O` | Typing text into the file. |
| **Visual** | `v`<br> `V` enters Visual Line mode <br> `Ctrl+v` enter Visual Block mode | Selecting and highlighting text blocks. |
| **Command** | `:` | Starts a command from Normal mode. |

## 🧭 Navigation (Normal Mode)
| Keystroke | Action |
| :--- | :--- |
| `h`, `j`, `k`, `l`, `arrow keys` | Left, Down, Up, Right. |
| `w` | Jump to next word. |
| `W` | Jump to next word separated by space. |
| `b` | Go to previous word. |
| `B` | Jump to previous word (separated by space). |
| `e` | Jump to the end of a word. |
| `0` | Go to the beginning of the line. |
| `$` | Go to the end of a line. |
| `%` | When focusing on a bracket, go to its pair. |
| `t[symbol]` | Jumps to the symbol before the specified one. |
| `f[symbol]` | Jumps to the specified symbol. |
| `gg` | Jump to the start of the file. |
| `G` | Jumps to the end of the file. |
| `:n` or `nG` | Jump to line n. |
| `/word` | Search for word. |
| `?word` | Same search but backwards. |
| `n` | Jump to next occurrence. |
| `N` | Go to previous occurrence. |
| `*` | Search forward for the next occurrence of the focused word. |
| `#` | Search backward for the previous occurrence of the focused word. |
| `m[char]` | Make the char a waypoint at the current location of the cursor. |
| `'[char]` | Jump the cursor back to that waypoint. |
| `zz` | Centers the cursor in the middle of the screen. |

## ✂️ Editing & Manipulation (Normal Mode)
| Keystroke | Action |
| :--- | :--- |
| `d` | Delete. |
| `dd` | Delete (cut) the current line. |
| `D` | Delete the rest of the line. |
| `dw` | Delete the rest of the word. |
| `diw` | Delete inside a word. |
| `d0` | Deletes everything from the beginning of the line. |
| `d$` | Delete everything until the end of the line. |
| `d%` | Delete anything between the brackets. |
| `dt[symbol]` | Deletes anything up to that symbol. |
| `y` | Yank (copy) operator. |
| `yy` | Yank (copy) the current line. |
| `p` | Paste the deleted or yanked text. |
| `P` | Paste before/above the cursor. |
| `c` | Delete the selection and enter Insert Mode. |
| `cc` | Delete the line and enter Insert Mode. |
| `C` | Delete the rest of the line and enter Insert Mode. |
| `ciw` | Change inside a word. |
| `ci[symbol]` | Change everything between the symbols. |
| `s` | Replace current selection. |
| `u` | Undo the last action. |
| `Ctrl+r` | Redo. |
| `number + command` | Executes the command a specific number of times (e.g., `5dd` deletes 5 lines). |
| `>>` | Indents the line to the right. |
| `<<` | Indents the line to the left. |
| `==` | Auto indents current line. |
| `gg=G` | Auto indent the whole file. |
| `:%s/word1/word2/g` | Replaces every occurrence of word1 with word2. |
| `.` | Executes the last command. |

## 💾 Saving & Quitting (Command Mode)
| Command | Action |
| :--- | :--- |
| `:w` | Save (write) the file. |
| `:q!` | Quit without saving (force quit). |
| `:wq` | Save and quit. |

## ✍️ Entering Insert Mode (From Normal Mode)
| Keystroke | Action |
| :--- | :--- |
| `i` | Insert text **before** the cursor. |
| `I` | Insert text at the **beginning** of the current line. |
| `a` | Append text **after** the cursor. |
| `A` | Append text at the **end** of the current line. |
| `o` | Open a new line **below** the current line and enter Insert mode. |
| `O` | Open a new line **above** the current line and enter Insert mode. |
| `c` | Delete the selection and enter Insert Mode. |
| `cc` | Delete the line and enter Insert Mode. |
| `C` | Delete the rest of the line and enter Insert Mode. |

## 🛠️ Useful Settings (Command Mode or `.vimrc`)
| Command | Description |
| :--- | :--- |
| `:set number` | Activates standard line numbers. |
| `:set relativenumber` | Displays line numbers relative to the current line. |
| `:set mouse=a` | Allows mouse usage within vim. |
| `:set tabstop=n` | Sets how many columns of whitespace a tab uses (replace 'n' with a number). |
| `:set shiftwidth=n` | Sets the number of spaces used for indentation. |
| `:set autoindent` | Automatically matches the indentation of the previous line. |
| `:colorscheme` | Used to change the visual color scheme. |

## 📼 Macros & Registers
| Command | Description |
| :--- | :--- |
| `:reg` | List all registers. |
| `"[n]yy` | Copy the current line into register [n]. |
| `"[n]p` | Paste the content of the register [n]. |
| `"+` | Special register that represents the system clipboard. |
| `"0` | Special register that contains the last thing actually copied. |
| `q[char]` | Start recording a macro into register [char]. |
| `q` | Quit recording the macro. |
| `@[char]` | Execute the macro from register [char]. |

## 🔌 Neovim & Plugins
| Command | Description |
| :--- | :--- |
| `sudo apt install neovim` | Install neovim. |
| `~/.config/nvim/init.vim` | Neovim config file where plugins are stored. |
| `vim-plug` | Popular plugin manager used to install plugins. |
| `call plug#begin()` <br> `Plug 'link'` <br> `call plug#end()` | Required syntax block inside the config file to define which plugins to load. |
| `:PlugInstall` | Install actual plugins. |