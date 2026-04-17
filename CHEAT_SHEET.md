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
| `mv` | *None* | Move or rename files/directories. If given multiple arguments, it moves all files into the last provided argument (which must be a directory) | `mv old.txt new.txt` |
| `cp` | *None* | Copy files or directories. | `cp file.txt /backup/` |
| `file` | *None* | Determine the true file type based on its contents (magic bytes), ignoring the extension. | `file script.txt` |

## 🔍 3. Text Processing & Searching
| Command | Common Flags & Meanings | Description | Example |
| :--- | :--- | :--- | :--- |
| `cat` | *None* | Print the content of a file to the terminal. | `cat config.json` |
| `echo` | *None* | Print text to the terminal. <br> used with `>` for overwriting <br> used with `>>` for appending | `echo "Hello" >> log.txt` |
| `grep` | `-i` (case-insensitive)<br>`-o` (only matching text)<br>`-A N` (show N lines After)<br>`-B N` (show N lines Before)<br> `-C N`(show N lines Before and After) <br> `-c` count matching lines | Search for specific patterns within files. | `grep -i "error" log.txt` |
| `less` | `/pattern` (search forward)<br>`n` (next match)<br>`Shift+n` (previous match) <br>`q` (quit) <br>`k`, `j`, `Up/Down Arrows` (move up and down) | Page through output or large files interactively. | `less massive_data.csv` |
| `more` | same as `less` | same as `less` | `more massive_data.csv` |
| `tr` | `-d` (delete characters) | Translate, or delete characters from standard input. | `cat log.txt \| tr 'a-z' 'A-Z'` |
| `cut` | `-d` (delimiter)<br>`-f` (field/column) | Extracts sections from each line based on a delimiter. Fields can be selected by index: `1` (first), `1-3` (range), `1,3` (specific), or `3-` (onwards). **Note:** It splits literally, so it is not a robust CSV parser if fields contain escaped commas. | `cut -d ',' -f 1,3 data.csv` |
| `sed` | `-e` (chain expressions) | Stream editor. Substitutes text using regex. Syntax: `s/old/new/`. You can change the delimiter `/` to `#` or `@` if your text contains slashes. | `sed 's/error/warning/' log.txt` |
| `awk` | `-F` (set delimiter) | Powerful text processing language. `$0` prints the whole line, `$1` prints the first column. Supports conditionals and `printf` formatting. | `awk -F: '$1=="root" {print $7}' /etc/passwd` |
| `sort` | *None* | Sorts lines of text input alphabetically (or numerically with flags). | `sort data.txt` |
| `uniq` | `-c` (count frequency) | Filters out adjacent duplicate lines. **Must** be used on sorted data to work properly. Use `-c` to count occurrences. | `sort data.txt \| uniq -c` |
| `wc` | `-l` (lines)<br>`-w` (words)<br>`-c` (characters) | Word count utility. Outputs the number of lines, words, and characters in a file or piped input. | `wc -l script.sh` |

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
|`yes`|**None**|Outputs 'y' repeatedly; useful to pipe to software that asks for multiple confirmations. | `yes \| rm -i *.txt`|
|`#`|**None**|Marks the start of a comment. Everything after this on a line is ignored by the shell.|`# This is a comment`|
|`$1`,`$2`,etc.|**None**|Positional parameters. The variable takes the first (or second, third) provided argument.|`echo first arg is $1`|
|`$@`|**None**|An array that expands to include all arguments passed to the script.|`for arg in "$@"; do`|
|`[[ -n $1 ]]` | `-n` nonzero length | A test condition used to check if a string or argument is set and not empty|`[[ -n $1 ]]`|
|`if [[ -n "$1" ]]; then` <br> body of the if <br> `else` <br> body of the else <br> `fi`|**None**|Evaluates a condition. If true, it runs the then body; otherwise, it can run an else body.|`if [[ -n "$1" ]]; then` <br> `echo "Set"` <br> `else` <br> `echo "Empty"`<br> `fi`|
|`name(){` <br> body <br> `}`|**None**|The syntax to define a function. Functions act like their own mini-programs within the script.|`greet (){` <br> `echo "hi $1"` <br> `}`|
|`local`|**None**|Variables in bash are global by default. Use the local keyword to make them local to the function|`local var="value"`|
|`return`|**None**|Functions automatically return the exit code of the last command inside. You can manually set the code using the return keyword.|`return 0`|
|`""`|**None**|Allows for variable expansion.|`echo "Hello $USER"`|
|`''`|**None**|Does not allow for variable expansion; treats everything literally.|`echo 'Hello $USER'`|
|`[[ -f file ]]`| `-f` regular file|A test condition used to check if a specific path exists and is a regular file.|`[[ -f ./script.sh ]]`|
|`while [[ cond ]]; do` <br> body <br> `done`|**None**|The syntax for a while loop. Runs as long as the condition is true.|`while [[ $x -gt 0 ]]; do` <br> `echo $x` <br> `done`|
|`until [[ cond ]]; do` <br> body <br> `done`|**None**|The syntax for an until loop. Runs as long as the condition is false.|`until [[ $x -eq 0 ]]; do` <br> `echo $x` <br> `done`|
|`if command; then`|**None**|if can execute a command directly instead of using [[ ]]. It checks its exit code and executes the then segment if the exit code was success (0).|`if grep "error" log; then` <br> `echo "Found!"` <br> `fi`|
|`true`,`false`|**None**|Commands in bash that just return exit codes  (0 for true, 1 for false). Very useful for infinite loops.|`while true; do` <br> `echo "Infinite"` <br> `done`|
|`{a..f}`|**None**|Brace expansion. Expands to a sequence from the starting value to the ending value (inclusive).|`for letter in {a..f}; do`|
|`(( ))`|**None**|Math and arithmetic syntax in bash. It is aware of variables, so there is no need for the $ prefix inside the parentheses.|`(( total = x + 5 ))`|
|`for (( i=0; i<max; i++ )); do` <br> body <br> `done`|**None**|C-style for loops in bash. They are a reliable and fast way to iterate a specific number of times.|`for (( i=0; i<5; i++ )); do` <br> `echo $i` <br> `done`|
|`read`|`-r`(raw input) <br> `-p` prompt |Reads user input. Use `-r` by default to prevent escaping issues.|`read -r -p "Name: " var`|
|`while read -r line; do` <br> body <br> `done`|**None**|Used to read a whole document line-by-line. read stops when it finds a newline character; if a file doesn't end with a newline, the last bit of data can be lost.|`while read -r line; do` <br> `echo "$line"` <br> `done < file.txt`|
|`[[ -n $line ]]`|`-n` (nonzero length)|Tests if the line variable has some data in it. Used alongside read to prevent losing the last line of a file if it lacks a trailing newline character.|`while read -r line \|\| [[ -n "$line" ]]; do`|
|`:`,`true`|**None**|A null command that does nothing. If a loop or if body is empty, Bash considers it an error. You can use : or true to safely "fill" it.|`while read -r line; do` <br> `:` <br> `done`|
|`<`|**None**|Input redirection. Tells a program to read its input from a specified file rather than from the terminal|`program < file.txt`|
|`$#`|**None**|A special variable that stores exactly how many arguments are given to a script or function.|`if [[ $# -eq 0 ]]; then`|
|`&0`,`&1`,`&2`|**None**|File descriptors used to manage data streams. &0 is standard input, &1 is standard output, and &2 is standard error.|`command > out.txt 2>&1`|
|`exit`|**None**|Stops the entire script and sets an exit code. Inside a script, outside a function, you cannot use return; the solution is to use exit (code).|`exit 1`|
|`elif`|**None**|Short for "else if". Used in if statements to chain multiple conditional checks together.|`elif [[ $var == 2 ]]; then`|

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

## ⚙️ 9. Advanced data and execution
| Command | Common Flags & Meanings | Description | Example |
| :--- | :--- | :--- | :--- |
|`case $var in` <br> `pattern)` <br> body <br> `;;` <br> `*)` <br> default <br> `;;` <br> `esac` | **None** | The syntax for a case statement. The * acts as a default, catch-all pattern. Normally, after finding a match and hitting ;;, it will not continue searching for other matches. | `case $1 in` <br> `start)` <br> `echo "starting"` <br> `;;` <br> `*)` <br> `echo "Unknown"` <br> `;;` <br> `esac`|
|`;&`|**None**|Used instead of ;;. It falls through and executes the body of the very next branch, no matter if its pattern matches or not.|`pattern1)` <br> body <br> `;&`|
|`;;&`|**None**|Used instead of ;;. It continues through all remaining branches and evaluates their patterns, executing the bodies of any that also apply/match.|`pattern1)` <br> body <br>`;;&`|
| `arr=(a b)` <br> `arr+=(c)` | *None* | Create an indexed array , or append new elements to an existing one. | `fruits=(apple kiwi)`<br>`fruits+=(orange)` |
| `${arr[n]}` <br> `${arr[-1]}` | *None* | Access an element at index `n`Use `-1` to easily grab the last element. | `echo ${fruits[1]}` |
| `"${arr[@]}"` | *None* | Expands to all elements safely. **Always use this version when writing `for` loops**. | `for i in "${arr[@]}"; do` |
| `new=("${arr[@]}")` | *None* | Copies an entire existing array into a new one. | `copy=("${fruits[@]}")` |
| `${#arr[@]}` | *None* | Returns the total number of elements currently in the array. | `echo ${#fruits[@]}` |
| `declare -A arr` | `-A` (associative) | Explicitly declares an associative array (key-value pairs). This is **mandatory**; you cannot create them on the fly. | `declare -A roles` |
| `arr[key]="val"` | *None* | Assigns a value to a specific string key. | `roles[admin]="Alice"` |
| `${arr[key]}` <br> `${arr[$var]}` | *None* | Accesses the value associated with a key. If the key is invalid, it returns an empty string. Use `$var` to use a variable's value as the key. | `echo ${roles[$user]}` |
| `"${!arr[@]}"` | *None* | Expands to all the **keys** of the associative array. Use this to loop over the keys. | `for key in "${!arr[@]}"; do` |
| `IFS` | *None* | Internal Field Separator. A built-in special variable determining how to break up arguments and split words. Defaults to space, tab, and newline.Can be set to other characters like `,` or `:`. | `IFS=','` |
| `( )` | *None* | Subshell execution. Everything executed between parentheses runs in a subshell. Variables or changes created inside are lost outside of it (local scope). | `(cd /tmp && ls)` |
| `` `cmd` `` | *None* | The old, legacy syntax for command substitution. Avoid this, as nesting them requires complex escaping. | `` echo `echo \`whoami\`` `` |
| `$(cmd)` | *None* | Command substitution (modern). Runs the command in a **subshell**. Any global variables modified inside it are lost as soon as it ends. It is very easy to nest. | `echo $(echo $(whoami))` |
| `{ cmd; }` | *None* | Command grouping. Groups commands together but runs them in the **main shell** (no subshell). Variable modifications made inside remain permanent. Note the required spaces and semicolon. | `{ func; }` |
| `$((a + b))` | *None* | Arithmetic expansion. Evaluates math. Variables inside do not need the `$` prefix. | `echo $((x + 5))` |
| `**` | *None* | Exponentiation operator (power). | `echo $((5**2))` |
| `<<` / `>>` | *None* | Bitwise left and right shift operators. | `$((1 << 5))` |
| `a > b ? a : b` | *None* | Ternary operator. Acts like an inline if-else statement. | `max=$((a>b?a:b))` |
| `10#` | *None* | Forces a number to be evaluated in base 10. Bash normally treats numbers starting with `0` as octal (base 8). | `echo $((10#08))` |
| Math Exit Codes | *None* | If the mathematical result is `0`, the command returns a failure exit code (`1`). If non-zero, it returns success (`0`). Beware when using `set -e`! | `((0))` (fails)<br>`((1))` (succeeds) |
| `<(cmd)` <br> `>(cmd)` | *None* | Process substitution. Runs a command and treats its input/output as a temporary file. Perfect for commands that require file arguments instead of standard input. | `diff <(ls dir1) <(ls dir2)` |
| `<<<` | *None* | Here string. Feeds a string or variable directly into a command's standard input. A cleaner, safer alternative to piping `echo "$var" | cmd`. | `while read -r word; do ... done <<< "$words"` |
| `|` (Subshell Trap) | *None* | **Warning:** Everything to the right of a pipe is executed in a **subshell**. Any variable modifications made after a pipe are lost when the command finishes! | `cat file \| while read x; do var=$x; done` (var is lost) |
|`shift`|**None**|Move the array of arguments by one|`shift`|
---
*Note: This cheat sheet is a living document and will expand as I cover more advanced topics like awk, sed, find, and specific bash parameters.*
