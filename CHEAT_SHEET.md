# 💻 Bash & Linux Command Cheat Sheet

This document serves as a quick reference guide for all the command-line tools, utilities, and shortcuts learned throughout the course. I update this list as I progress through new modules.

## 📁 1. Navigation & Directory Operations
| Command | Common Flags & Meanings | Description | Example |
| :--- | :--- | :--- | :--- |
| `pwd` | *None* | Print working directory (current path). | `pwd` |
| `ls` | `-a` (show hidden/all) <br> `-l` (long listing) | List directory contents. | `ls -a` |
| `cd` | `-` (jump to previous dir)<br> `..` (jump to parent dir) | Change directory. | `cd /var/log` |
| `whoami` | *None* | displays logged user | `whoami` |
| `uname` | `-a` (all information) | displays system's name | `uname -a` |

## 📝 2. File Manipulation
| Command | Common Flags & Meanings | Description | Example |
| :--- | :--- | :--- | :--- |
| `touch` | *None* | Create an empty file or update timestamps. | `touch new_script.sh` |
| `rm` | `-i` (interactive/ask first)| Remove files or directories. | `rm -i file1.txt` |
| `mv` | *None* | Move or rename files/directories. | `mv old.txt new.txt` |
| `cp` | *None* | Copy files or directories. | `cp file.txt /backup/` |
| `file` | *None* | Determine the true file type based on its contents (magic bytes), ignoring the extension. | `file script.txt` |

## 🔍 3. Text Processing & Searching
| Command | Common Flags & Meanings | Description | Example |
| :--- | :--- | :--- | :--- |
| `cat` | *None* | Print the content of a file to the terminal. | `cat config.json` |
| `echo` | *None* | Print text to the terminal. <br> used with `>` for overwriting <br> used with `>>` for appending | `echo "Hello" >> log.txt` |
| `grep` | `-i` (case-insensitive)<br>`-o` (only matching text)<br>`-A N` (show N lines After)<br>`-B N` (show N lines Before)<br> `-C N`(show N lines Before and After) | Search for specific patterns within files. | `grep -i "error" log.txt` |
| `less` | `/pattern` (search forward)<br>`n` (next match)<br>`Shift+n` (previous match) <br>`q` (quit) <br>`k`, `j`, `Up/Down Arrows` (move up and down) | Page through output or large files interactively. | `less massive_data.csv` |
| `more` | same as `less` | same as `less` | `more massive_data.csv` |
| `tr` | `-d` (delete characters) | Translate, or delete characters from standard input. | `cat log.txt \| tr 'a-z' 'A-Z'` |

## ⌨️ 4. Terminal Shortcuts & History
| Shortcut / Command | Description |
| :--- | :--- |
| `CTRL + L` | Clears the terminal screen (same as `clear` command). |
| `clear` | Clears the terminal screen |
| `Up / Down Arrows` | Navigate back and forth through the command history. |
| `TAB` | Autocompletes commands, file names, or directory names. |
| `history` | Prints the entire history of executed commands. |

## 🃏 5. Globbing & Regular Expressions

### Shell Globbing (File Name Matching)
| Wildcard | Description | Example |
| :--- | :--- | :--- |
| `*` (Asterisk) | Matches zero or more characters of any type. Useful for acting on multiple files at once. | `rm *.txt` (removes all .txt files)<br>`ls doc*` (lists files starting with "doc") |

### Basic Regular Expressions (Text Matching)
| Symbol | Description | Example |
| :--- | :--- | :--- |
| `^` (Caret) | Matches the beginning of the line | `grep '^error' log.txt` (finds lines starting with "error") |
| `$` (Dollar) | Matches the end of the line | `grep 'done$' log.txt` (finds lines ending with "done") |
| `.` (Dot) | Matches exactly 1 character | `grep 'd.g' file.txt` (finds "dog", "dig", "dug") |

## ⚙️ 6. Scripting Fundamentals 
| Command | Common Flags & Meanings | Description | Example |
| :--- | :--- | :--- | :--- |
| `chmod` | `+x` (make executable)<br>`-R` (recursive) | Change file/directory permissions. | `chmod +x script.sh` |
| `bash` | `-n` (check for syntax errors) | Run a script directly through the bash interpreter (no execute permissions needed). | `bash script.sh` |
| `./` | *None* | Execute a file located in the current directory (requires `+x` permission and a shebang). | `./script.sh` |
| `#!` | *None* | The "Shebang". Placed on the first line of a script to define the interpreter for the OS. | `#!/usr/bin/env bash` |
|`for thing in list; do ` <br> body of the for loop <br> `done`|*None*|the syntax for a for loop| `for thing in foo bum bash; do ` <br> `thing is $thing` <br> `done`|
|`read`|`-p "text"` displays a prompt|Displays text and reads user input from the terminal, storing it in a variable|`read -p "Name: " var`|
|`yes`|**None**|Outputs 'y' repeatedly; useful to pipe to software that asks for multiple confirmations. | `yes \| rm -i *.txt`|
|`#`|**None**|Marks the start of a comment. Everything after this on a line is ignored by the shell.|`# This is a comment`|
|`$1`,`$2`,etc.|**None**|Positional parameters. The variable takes the first (or second, third) provided argument.|`echo first arg is $1`|
|`$@`|**None**|An array that expands to include all arguments passed to the script.|`for arg in "$@"; do`|
|`[[ -n $1 ]]` | `-n` nonzero length | A test condition used to check if a string or argument is set and not empty|`[[ -n $1 ]]`|
|`if [[ -n "$1" ]]; then` <br> body of the if <br> `else` <br> body of the else <br> `fi`|**None**|Evaluates a condition. If true, it runs the then body; otherwise, it can run an else body.|`if [[ -n "$1" ]]; do` <br> `echo "Set"` <br> `else` <br> `echo "Empty"`<br> `fi`|
|`name(){` <br> body <br> `}`|**None**|The syntax to define a function. Functions act like their own mini-programs within the script.|`greet (){` <br> `echo "hi $1"` <br> `}`|
|`local`|**None**|Variables in bash are global by default. Use the local keyword to make them local to the function|`local var="value"`|
|`return`|**None**|Functions automatically return the exit code of the last command inside. You can manually set the code using the return keyword.|`return 0`|
|`""`|**None**|Allows for variable expansion.|`echo "Hello $USER"`|
|`''`|**None**|Does not allow for variable expansion; treats everything literally.|`echo 'Hello $USER'`|
|`[[ -f file ]]`| `-f` regular file|A test condition used to check if a specific path exists and is a regular file.|`[[ -f ./script.sh ]]`|
|`while [[ cond ]]; do` <br> body <br> `done`|**None**|The syntax for a while loop. Runs as long as the condition is true.|`The syntax for a while loop. Runs as long as the condition is true.` <br> `echo $x` <br> `done`|
|`until [[ cond ]]; do` <br> body <br> `done`|**None**|The syntax for an until loop. Runs as long as the condition is false.|`until [[ $x -eq 0 ]]; do` <br> `echo $x` <br> `done`|
|`if command; then`|**None**|if can execute a command directly instead of using [[ ]]. It checks its exit code and executes the then segment if the exit code was success (0).|`if grep "error" log; then` <br> `echo "Found!"` <br> `fi`|
|`true`,`false`|**None**|Commands in bash that just return exit codes  (0 for true, 1 for false). Very useful for infinite loops.|`while true; do` <br> `echo "Infinite"` <br> `done`|
|`{a..f}`|**None**|Brace expansion. Expands to a sequence from the starting value to the ending value (inclusive).|`for letter in {a..f}; do`|
|`(( ))`|**None**|Math and arithmetic syntax in bash. It is aware of variables, so there is no need for the $ prefix inside the parentheses.|`(( total = x + 5 ))`|
|`for (( i=0; i<max; i++ )); do` <br> body <br> `done`|**None**|C-style for loops in bash. They are a reliable and fast way to iterate a specific number of times.|`for (( i=0; i<5; i++ )); do` <br> `echo $i` <br> `done`|
|`read`|`-r`(raw input)|The -r flag prevents backslashes from being treated as escape characters. By itself, read only reads the first line of input.|`read -r line`|
|`while read -r line; do` <br> body <br> `done`|**None**|Used to read a whole document line-by-line. read stops when it finds a newline character; if a file doesn't end with a newline, the last bit of data can be lost.|`while read -r line; do` <br> `echo "$line"` <br> `done < file.txt`|
|`[[ -n $line ]]`|`-n` (nonzero length)|Tests if the line variable has some data in it. Used alongside read to prevent losing the last line of a file if it lacks a trailing newline character.|`while read -r line \|\| [[ -n "$line" ]]; do`|
|`:`,`true`|**None**|A null command that does nothing. If a loop or if body is empty, Bash considers it an error. You can use : or true to safely "fill" it.|`while read -r line; do` <br> `:` <br> `done`|
|`<`|**None**|Input redirection. Tells a program to read its input from a specified file rather than from the terminal|`program < file.txt`|
|`$#`|**None**|A special variable that stores exactly how many arguments are given to a script or function.|`if [[ $# -eq 0 ]]; then`|
|`$0`,`$1`,`$2`|**None**|File descriptors used to manage data streams. &0 is standard input, &1 is standard output, and &2 is standard error.|`command > out.txt 2>&1`|
|`exit`|**None**|Stops the entire script and sets an exit code. Inside a script, outside a function, you cannot use return; the solution is to use exit (code).|`exit 1`|
|`elif`|**None**|Short for "else if". Used in if statements to chain multiple conditional checks together.|`elif [[ $var == 2 ]]; then`|
|`case $var in` <br> `pattern)` <br> body <br> `;;` <br> `*)` <br> default <br> `;;` <br> `esac` | **None** | The syntax for a case statement. The * acts as a default, catch-all pattern. Normally, after finding a match and hitting ;;, it will not continue searching for other matches. | `case $1 in` <br> `start)` <br> `echo "starting"` <br> `;;` <br> `*)` <br> `echo "Unknown"` <br> `;;` <br> `esac`|
|`;&`|**None**|Used instead of ;;. It falls through and executes the body of the very next branch, no matter if its pattern matches or not.|`pattern1)` <br> body <br> `;&`|
|`;;&`|**None**|Used instead of ;;. It continues through all remaining branches and evaluates their patterns, executing the bodies of any that also apply/match.|`pattern1)` <br> body <br>`;;&`|

## ⚙️ 7. Environment & Shell Customization
| Command | Common Flags & Meanings | Description | Example |
| :--- | :--- | :--- | :--- |
| `alias` | `name="cmd"` (create shortcut)<br>`-p` (print all aliases) | Create a custom shortcut for a command. | `alias update="sudo apt update"` |
| `unalias` | *None* | Remove a previously created alias. | `unalias update` |
| `var=value` | *None* | Assign a value to a variable (NO spaces around the `=`). | `name="John"` |
| `unset` | *None* | Delete a previously defined variable from the shell session. | `unset name` |
| `$(cmd)` | *None* | Command Substitution: evaluates the command inside and replaces it with its output. | `files=$(ls -a)` |
|`$?`|*None*|variable that stores the exit code of the last command|`echo $?`|

## 📚 8. Help & Command Identification
| Command | Common Flags & Meanings | Description | Example |
| :--- | :--- | :--- | :--- |
| `man` | `N` (specific section)<br>`-f` (short desc & section) | Open the manual for an external command. | `man 5 passwd`<br>`man man` |
| `help` | *None* | Get documentation for Bash **built-in** commands. | `help cd` |
| `which` | *None* | Locate the executable file of an external command on the system. | `which grep` |
| `type` | `-a` (show all locations and types) | Identify if a command is a built-in, an alias, or an external file. | `type -a echo` |
| `compgen` | `-b` (list all built-ins) | List available commands or built-ins. | `compgen -b` |

---
*Note: This cheat sheet is a living document and will expand as I cover more advanced topics like awk, sed, find, and specific bash parameters.*
