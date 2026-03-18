# ⌨️ Vim Mastery Cheat Sheet

This document tracks my progress learning `vim`, the ubiquitous terminal text editor. 

## 🔄 Core Modes
| Mode | Key(s) to Enter | Description |
| :--- | :--- | :--- |
| **Normal** | `ESC` | Default mode for navigation, deletion, and copying. |
| **Insert** | `i`, `I`, `a`, `A`, `o`, `O` | Typing text into the file. |
| **Visual** | `v`, `V`, `CTRL+V` | Selecting and highlighting text blocks. |

## 🧭 Navigation (Normal Mode)
| Keystroke | Action |
| :--- | :--- |
| `h`, `j`, `k`, `l`, `arrow keys` | Left, Down, Up, Right. |
| *(more to be added)* | |

## ✂️ Editing & Manipulation (Normal Mode)
| Keystroke | Action |
| :--- | :--- |
| `dd` | Delete (cut) the current line. |
| `yy` | Yank (copy) the current line. |
| `p` | Paste the deleted or yanked text. |
| `u` | Undo the last action. |

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