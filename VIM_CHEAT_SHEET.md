# ⌨️ Vim Mastery Cheat Sheet

This document tracks my progress learning `vim`, the ubiquitous terminal text editor. 

## ⚙️ Installation & Setup
| Command / Concept | Description |
| :--- | :--- |
| `sudo apt install vim` | Installs vim. |
| `vim` or `vi` | Run these to check if vim is installed. |
| `.vimrc` | The configuration file where you can save your vim settings permanently. |
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
| **Visual** | `v`, `V`, `CTRL+V` | Selecting and highlighting text blocks. |
| **Command** | `:` | Starts a command from Normal mode. |

## 🧭 Navigation (Normal Mode)
| Keystroke | Action |
| :--- | :--- |
| `h`, `j`, `k`, `l`, `arrow keys` | Left, Down, Up, Right. |

## ✂️ Editing & Manipulation (Normal Mode)
| Keystroke | Action |
| :--- | :--- |
| `dd` | Delete (cut) the current line. |
| `yy` | Yank (copy) the current line. |
| `ctrl + y` | Yank (copy) the current line. |
| `p` | Paste the deleted or yanked text. |
| `u` | Undo the last action. |
| `number + command` | Executes the command a specific number of times (e.g., `5dd` deletes 5 lines). |
| `ctrl+r` | redo |
| `d` | delete |
| `y` | copy |
| `p` | paste |
| `ctrl + p` | paste before/above the cursor |
| `c` | delete the selection and enter Insert Mode |
| `cc` | delete the line and enter Insert Mode |
| `ctrl + d` | delete the rest of the line |
| `ctrl + c` | delete the rest of the line and enter Insert Mode |
| `s` | replace current selection |

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
| `c` | delete the selection and enter Insert Mode |
| `cc` | delete the line and enter Insert Mode |
| `ctrl + c` | delete the rest of the line and enter Insert Mode |

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