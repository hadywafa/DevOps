# Linux Summary

## index

- `00:00` Introduction:
- `01:20` History:  of Unix/Linux
- `29:55` Linux:  Distributions
- `48:45` Installation:
- `56:17` Basic:  Commands
- `01:29:07`:  Text Files
- `01:42:55`:  Unix Philosophy
- `02:06:53`:  More on Text Files
- `02:09:45`:  Terminal vs Shell
- `02:37:36`:  Shell Expansion
- `02:34:12`:  Shell Variables
- `03:07:32`:  Pipes, Filters and Redirection
- `03:24:55`:  grep command
- `03:41:41`:  tr and cut commands
- `03:50:38`:  User and Group Management
- `04:40:35`:  File Management
- `04:58:53`:  Filesystem Hierarchy Specifications (FHS)
- `05:26:11`:  File types, head, tail, more, less, mkdir, rmdir, rm
- `05:36:34`:  Finding files
- `05:48:39`:  File Archive and Compression
- `06:04:33`:  File Ownership and Permissions
- `06:34:38`:  Managing Linux Processes
- `07:20:10`:  Package Management
- `08:07:20`:  Connecting to Remote Servers (ssh, wget, curl, etc.)
- `09:21:50`:  Introduction to Shell Scripts
- `11:18:20`:  Last Words

## Architecture Principle for App in unix

- **Small is Beautiful**
- **Prototype as Soon as Possible**
- **Choose Portability Over Efficiency**
- **Store Data in Flat Text Files**
- **Use Software Leverage**
- **Use Shell Scripts to Increase Leverage and Portability**
- **Avoid Captive User Interfaces**
- **Make Every Program a Filter**

## basic Commands

- `pwd` : Show current dir
  - examples
    - **pwd**
    - **/usr/bin/pwd**

- `ls` or `ll` : List current dir
  - parameters
    - `-a` show hidden files
    - `-l` show result vl
    - `-F` show `/` at end of dir.
  - examples
    - **ls**
    - **ls -a**
    - **ls -a -l**
    - **ls -a -l -F**
    - **ls -alF**

- `cd` : Change current dir
  - parameters
    - `.` current dir
    - `..` parent dir
    - `~` home dir
  - examples
    - **cd .**
    - **cd ..**
    - **cd ~** home dir
    - **cd /** base dir

- `clear` or `ctrl + l` : Clear console
  - examples
    - **clear**
    - **ctrl + l**

- `type` or `--help` : Command info
  - examples
    - **type -a [command]**
    - **[command] --help**

- `whoami` : get current user
  - parameters
  - examples

- `echo` : print
  - parameters
  - examples
    - echo "Hello Linux"

- `history` : print all used commands

- `ip`: print ip

- `mkdir` : create dir
  - argument
    - **[dir-name]**
  - parameters
  - examples
    - **mkdir TestDir**

- `rmdir` : remove empty dir
  - examples
    - **rmdir testDir**

- `touch` : create file
  - used for:
    1. change timestamp of file
    1. if file file not exist it create it
    1. file type is just text empty file
  - argument
    - **[file-name]**
  - examples
    - **touch file1**

- `rm` : remove file or not empty dir
  - parameters
    - **-r** : remove fir dir and all its content
  - examples
    - **rm file1**
    - **rm -r testDir/**

- `cat` : show content of file
  - examples
    - **echo /etc/hosts**

- `cp` : copy files
  - parameters
    - [source-file] [target-dir-path]
  - examples
    - **cp /etc/hosts  /home/hady/**

- `which` : check where is command is located
  - examples
    - **which nano**

## Editing Text Files

### vi

- Command mode
  - `j` = ⬅️left
  - `k` = ➡️right
  - `h` = ⬆️up
  - `l` = ⬇️down
  - `:q` = exit

- Inset mode

### nano

- How to Open File
  - **nano [file-name]**
- How to Exist

## Managing Variables in Linux

### 1. Create Variables

- To create a variable in Linux, you simply assign a value to a variable name.
  - Example: `name="John"` creates a variable `name` with the value "John".

### 2. Read Variables

- To read the value of a variable, you prefix the variable name with a dollar sign `$`.
  - Example: `echo $name` prints the value of the variable `name`.

### 3. Print Variables

- You can print the value of a variable using commands like `echo`.
  - Example: `echo "Hello, $name"` prints "Hello, John" assuming `name` variable is set to "John".

### 4. Set Variables

- To set or change the value of a variable, you simply reassign it.
  - Example: `name="Alice"` changes the value of the `name` variable to "Alice".

### 5. Delete Variables

- You can delete a variable using the `unset` command.
  - Example: `unset name` deletes the `name` variable.

### 6. Readonly Variables

- You can make variables readonly using the `readonly` command.
  - Example: `readonly var=value` sets a variable `var` to "value" and makes it readonly.

### 7. Declare Variables

- The `declare` command is used to declare variables with attributes.
  - Example: `declare -i number=5` declares an integer variable `number` with the value 5.

### 8. Environment Variables

- To create an environment variable, you use the `export` command.
  - Example: `export PATH=$PATH:/usr/local/bin` adds `/usr/local/bin` to the existing `PATH` variable.

### 9. Array Variables

- Array variables hold multiple values under a single variable name.
  - Example: `fruits=("apple" "banana" "orange")` creates an array variable `fruits` with three elements.

### 10. Special Variables: $$ and BASHPID

- `$$` represents the process ID of the current shell.
  - Example: `echo $$` prints the PID of the current shell.
- `BASHPID` also represents the process ID of the current shell but is available in subshells.
  - Example: `echo $BASHPID` prints the PID of the current shell.

### 11. Expression Evaluation: expr

- The `expr` command evaluates expressions.
  - Example: `expr 5 + 3` evaluates to 8.

### 12. Variable Lifetime

- Variables have different lifetimes:
  - **Session Lifetime**: Variables created in a shell session persist until the session is closed.
  - **Shell Lifetime**: Variables created in a shell script or command persist until the shell process exits.

## Linux Expansions

### 1. Filename Expansion (Globbing)

- Replaces patterns with filenames in the current directory that match the pattern.
- Example: `ls *.txt` lists all files ending with `.txt`.

### 2. Brace Expansion

- Generates strings by expanding comma-separated patterns enclosed in braces `{}`.
- Example: `echo {one,two,three}` expands to `one two three`.

### 3. Parameter Expansion

- Allows manipulation of variables and their values.
- Example: `${var:-default}` expands to the value of `$var` if set, otherwise expands to `default`.

### 4. Arithmetic Expansion

- Evaluates mathematical expressions.
- Example: `echo $((2 + 2))` expands to `4`.

### 5. Command Substitution

- Replaces a command enclosed in backticks or `$()` with its output.
- Example: `echo "Today is $(date)"` expands to include the current date.

### 6. Tilde Expansion

- Replaces the tilde `~` with the path to the user's home directory.
- Example: `cd ~/Documents` expands to `cd /home/user/Documents`.

## Shell Types

there are two types of shell

1. Login Shell
    - needs credential before login to it
1. Non-Login Shell
    - doesn't need credential because it get it from base shell

- `echo $0` : To Know current shell type, if shell name has `-`before it then it is login sell else it non-login shell.

## Configuration Files in Linux Shells

### /etc/profile

- `/etc/profile` is a system-wide configuration file executed for login shells.
- It sets up environment variables and paths needed system-wide for all users.
- Changes made to this file affect the entire system and all users.
- Typically contains global settings and environment variables.

### ~/.bashrc

- `~/.bashrc` (or `.bashrc`) is a user-specific configuration file executed for interactive non-login shells.
- It is located in the user's home directory (`~`) and is not present by default.
- It sets up user-specific preferences, aliases, functions, and environment variables relevant to the user's session.
- Changes made to this file only affect the current user's shell environment.

### Usage

- **/etc/profile**:
  - Used to set system-wide environment variables like `PATH`, `LANG`, and `LC_*`.
  - Might load other system-wide configuration files or scripts located in `/etc/profile.d/`.
  - Ensures consistent configuration across the system by administrators.

- **~/.bashrc**:
  - Primarily used for customizing the user's shell environment according to their preferences.
  - Allows users to define aliases, functions, and customize their prompt.
  - Provides a space for users to set up environment variables or modify shell behavior for interactive sessions.

In summary, `/etc/profile` is a system-wide configuration file for login shells, setting up global environment variables, while `~/.bashrc` is a user-specific configuration file for interactive non-login shells, allowing users to customize their shell environment.

## Pipes, Filters, and Redirection in Linux

![alt text](/images/stdin-stdout-stderr.png)

### Standard Input (stdin), Standard Output (stdout), and Standard Error (stderr)

- In Linux, each process has three default streams:
  - **Standard Input (stdin, 0)**: The stream where a process reads input. By default, it is connected to the keyboard.
  - **Standard Output (stdout, 1)**: The stream where a process writes normal output. By default, it is connected to the terminal.
  - **Standard Error (stderr, 2)**: The stream where a process writes error messages. By default, it is also connected to the terminal.
- Redirection operators (`<`, `>`, `>>`) can be used to change the sources or destinations of these streams.
- Example: `command > output.txt 2>&1` redirects both stdout and stderr to the same file `output.txt`.

Pipes, filters, and redirection provide a powerful mechanism for manipulating data streams and performing various tasks efficiently on the Linux command line. They are fundamental concepts for shell scripting and everyday command-line usage.

### Redirection (`>`, `>>`,`2>`, `<`)

- Controls where the input comes from and where the output goes.
- Main redirection operators:
  - `>`: Redirects standard output (stdout) to a file, overwriting its contents if it already exists.
  - `2>`: Redirects standard error (stderr) to a file, overwriting its contents if it already exists.
  - `>>`: Redirects standard output (stdout) to a file, appending to its contents if it already exists.
  - `<`: Redirects standard input (stdin) from a file.
- Examples:
  - Output redirection: `ls > files.txt` lists files in the current directory and writes the output to a file named `files.txt`.
  - Error redirection: `ls asd 2> error.txt`   writes the error output to a file named `error.txt`.
  - Input redirection: `wc -l < textfile.txt` counts the number of lines in `textfile.txt` by redirecting its contents as input to the `wc` command.

### Filters

Filters are commands in Unix-like operating systems that process input data and produce output based on specific criteria. They are essential tools for text processing and manipulation. Here are some common filters along with information and examples:

- **`grep`**:
  - Searches for patterns in text.
  - Example: `grep "error" logfile.txt` searches for lines containing the word "error" in the file `logfile.txt`.

- **`sort`**:
  - Sorts lines of text alphabetically or numerically.
  - Example: `sort names.txt` sorts the lines in the file `names.txt` alphabetically.

- **`head`**:
  - Displays the beginning (head) portion of a file.
  - Example: `head -n 10 file.txt` displays the first 10 lines of the file `file.txt`.

- **`tail`**:
  - Displays the ending (tail) portion of a file.
  - Example: `tail -n 20 file.txt` displays the last 20 lines of the file `file.txt`.

- **`wc`** (word count):
  - Counts the number of lines, words, and characters in a file.
  - Example: `wc -l file.txt` counts the number of lines in the file `file.txt`.

- **`awk`** and **`sed`**:
  - Powerful text processing tools for pattern matching and manipulation.
  - Example: `awk '{print $1}' data.txt` prints the first column of data in the file `data.txt`.

- **`uniq`**:
  - Filters out adjacent duplicate lines.
  - Example: `uniq names.txt` filters out duplicate lines from the file `names.txt`.

- **`tr`** (translate):
  - Translates or deletes characters from the input stream.
  - Example:
    - `echo "Hello" | tr '[:lower:]' '[:upper:]'` converts lowercase letters to uppercase.
    - `echo "123456" | tr '123' 'ABC'` translates digits to letters.
    - `echo "hello world" | tr -d 'aeiou'` removes all vowels from the input.

- **`cut`**:
  - Removes sections from each line of files.
  - Example:
    - `cut -d':' -f1 /etc/passwd` extracts the first field from the `/etc/passwd` file using ':' as the delimiter.
    - `echo "John:Doe:25" | cut -d':' -f2` extracts the second field from the input
    - `cut -c1-5 file.txt` extracts the first 5 characters from each line of the file file.txt.

These filters can be combined in various ways using pipes (`|`) to create powerful text processing pipelines. For example, `grep` can be used to filter specific lines, and then `sort` can sort those lines alphabetically.

### Pipes (`|`)

- Connects the output of one command as the input to another command.
- Represented by the `|` symbol.
- Example:
  - `ls -l | grep ".txt"` lists files in the current directory and filters lines containing ".txt".
  - `head -n 50 /var/log/syslog | wc -w`
  - `head -n 50 /var/log/syslog | grep file1 | wc -l`
  - int1=$(head -n 50 /var/log/syslog | grep file1 | wc -l); echo $int1

## Notes

- terminal syntax is case-sensitive
- Directory path has `/` at its end
- any command is just app or script than i call when run it using its full path or sugar syntax
  - `/usr/bin/pwd` == `pwd`
- profile path :
  - `default:[user-name]@[machine-name]:~$` : `hady@devops-vm:~$`
- shell vs terminal
- don't forgot last `/` in `cp` command because it will rename the dir of you forgot that.
- `echo $?` : used to know the output status
- `echo $0` : To Know current shell type, if shell name has `-`before it then it is login sell else it non-login shell.
