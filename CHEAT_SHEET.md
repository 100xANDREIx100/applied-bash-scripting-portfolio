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
| `find` | `-type f` (files)<br>`-type d` (directories)<br>`-type l` (symlinks)<br>`-name` (search by name) | Searches recursively for files in a directory hierarchy. **Note:** The order of arguments matters! Always put the path first, then the filters. | `find . -type f -name "*.txt"` |
| `-exec` | *None* | A flag for `find` that executes a command on each file it finds. `{}` represents the current file. Must end with `\;` (one by one) or `+` (all at once). | `find . -name "*.bak" -exec rm {} \;` |
| `-print0` | *None* | A flag for `find` that separates output using a null byte instead of a newline. Crucial for handling file names that contain spaces. | `find . -type f -print0` |
| `xargs` | `-0` (read null bytes) | Takes standard input and passes it as arguments to another command. Used to batch process output. Use `-0` when pairing with `find -print0`. | `find . -name "*.txt" -print0 \| xargs -0 rm` |
| `nl` | *None* | Number lines. Reads a file or piped input and prints it to the terminal with line numbers added to the left side. | `nl script.sh` |

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

## 🐛 10. Execution and Debugging

| Command / Syntax | Common Flags & Meanings | Description | Example |
| :--- | :--- | :--- | :--- |
| `bash` | `-x` (debug/trace mode)<br>`-u` (nounset) | `-x` runs a script while printing every command before it executes. `-u` forces the script to fail if it encounters an undefined variable (by default, Bash just treats them as empty strings). | `bash -x script.sh`<br>`bash -u script.sh` |
| `set -x` <br> `set +x` | *None* | Turns debugging on (`-x`) and off (`+x`) for a specific section *inside* a script, rather than debugging the whole file. | `set -x`<br>`# broken code here`<br>`set +x` |
| `PS4` | *None* | A special environment variable that dictates what the debug prompt looks like when using `-x`. | `PS4='+ $LINENO: '` |
| `VAR=value cmd` | *None* | Sets an environment variable strictly for the duration of that single script or command run, without permanently adding it to your shell. | `DEBUG=1 ./script.sh` |
| `shellcheck` | *None* | A powerful external linter and static analysis tool. It scans your script and points out bugs, bad practices, and syntax errors before you even run it. | `shellcheck script.sh` |
| `set -o pipefail` | *None* | Changes pipeline behavior. Instead of returning the exit code of only the last command, the pipeline will fail if *any* command within it fails. | `set -o pipefail` |
| `${PIPESTATUS[@]}` | *None* | A special array holding the individual exit codes of *all* commands in the most recently executed pipeline. (Your notes show `*`, but `[@]` is generally safer for array expansion). | `cmd1 \| cmd2`<br>`echo "${PIPESTATUS[@]}"` |
| `time` | *None* | Measures how long a command takes to execute. Outputs `real` (actual wall-clock time), `user` (CPU time spent processing), and `sys` (CPU time spent in the kernel/system calls). | `time ./script.sh` |
| `top` | *None* | Displays real-time system statistics and resource usage (CPU, memory, and running processes). | `top` |

## 🏗️ 11. Code Architecture

| Command / Syntax | Common Flags & Meanings | Description | Example |
| :--- | :--- | :--- | :--- |
| `source` <br> `.` (dot) | `-p` selects a file from a defined variable | Reads and executes commands from a file in the *current* shell environment. Useful for loading functions or variables like a library. The code inside is executed immediately upon import. | `source ./library.sh`<br>`. ./library.sh` |
| `if ! (return 0 2>/dev/null); then` | *None* | A clever idiom to check if a script is being run directly. `return` fails if the script is run directly (rather than sourced). Put the code you only want executed directly inside the `then` block. | `if ! (return 0 2>/dev/null); then`<br>`echo "Run directly"`<br>`fi` |
| `name() (` <br> body <br> `)` | *None* | Defines a function that executes entirely within a **subshell** (using `()` instead of `{}`). Any variables modified or exported inside this function are safely destroyed when it finishes, protecting your global scope. | `sandbox() (` <br> `cd /tmp && ls` <br> `)` |
| `return 255` | *None* | Return codes in Bash are strictly limited to 8-bit integers (0 to 255). If you try to return 256, it wraps around to 0 (success)! | `return 1` |
| `2>&1 >/dev/null` | *None* | Sliences the standard output and returns the standard error as the standard output| `cmd > /dev/null 2>&1` |
---
*Note: This cheat sheet is a living document and will expand as I cover more advanced topics like awk, sed, find, and specific bash parameters.*
