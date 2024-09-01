# Bash-Scripting-Notes
This repository contains notes and example scripts based on what I learned from the Free Code Camp [Bash Scripting Tutorial for Beginners](https://www.youtube.com/watch?v=tK9Oc6AEnR4&t). It covers essential Bash scripting concepts, commands, and practical examples.

## Basic Bash/Linux/Unix Commands
- `ls` - Lists directory contents
- `cd` - Changes the current directory
- `pwd` - Prints the working directory
- `echo` - Displays text or the value of a variable in the terminal

  Examples:
  - Printing a simple string:
  ```
  echo Hello World!
  ```
  This command will output:
  ```
  Hello World!
  ```
  - Displaying the value of a variable:
  ```
  NAME="Julian"
  echo "Hello $NAME"
  ```
  This will output:
  ```
  Hello Julian
  ```
- `cat` - Concatenates and displays the contents of files in the terminal
  
  Examples:
  - Display the contents of a file:
  ```
  cat filename.txt
  ```
  This command will output the entire contents of filename.txt to the terminal.
  - Concatenate multiple files and display the result:
  ```
  cat file1.txt file2.txt
  ```
  This will display the contents of both file1.txt and file2.txt sequentially.

- `#! (shebang or hashbang)` - Used at the very beginning of a script to indicate which interpreter should be used to execute the script. The shebang is followed by the path to the interpreter.

  Example:
  ```
  #!/bin/bash
  ```

  This line tells the operating system to use the Bash shell (/bin/bash) to execute the script.

- `./` - Used to run a script or executable file located in the current directory.

  Example:
  ```
  ./script.sh
  ```

- `chmod (change mode)` - Used to change the permissions of files and directories. It allows you to specify who can read, write, or execute a file.

  <ins>File Permissions</ins>

  In Unix-like systems, each file and directory has a set of permissions for three categories of users:

    1. `Owner (u)` : The user who owns the file.
    2. `Group (g)` : Users who are part of the file's group.
    3. `Others (o)` : All other users.

  Permissions are typically represented as:

    - `r` (read): Allows reading the contents of the file or listing the contents of a directory.
    - `w` (write): Allows modifying the contents of the file or adding/removing files in a directory.
    - `x` (execute): Allows running the file as a program/script or entering a directory.

  <ins>Syntax</ins>

  The basic syntax of chmod is:
  ```
  chmod [permissions] [file/directory]
  ```

  Example:
  ```
  chmod u+x shelltest.sh
  ```

  <ins>Setting Permissions Using Symbols</ins>

  You can modify permissions using symbolic representations:

  - `+` : Adds a permission.
  - `-` : Removes a permission.
  - `=` : Sets the specified permission and removes others.

  For example:

  - `chmod u+x file.sh` : Adds execute permission for the owner.
  - `chmod g-w file.sh:` : Removes write permission for the group.
  - `chmod o=r file.sh:` : Sets the permissions for others to read-only.

  <ins>Setting Permissions Using Numbers</ins>

  Permissions can also be set using a numeric notation (octal numbers):

  - `r` = 4
  - `w` = 2
  - `x` = 1

  These numbers are added together to set the desired permissions. For example:

  - `chmod 755 file.sh` : Sets read, write, and execute permissions for the owner (7), and read and execute permissions for the group and others (5).
  - `chmod 644 file.sh` : Sets read and write permissions for the owner (6), and read-only permissions for the group and others (4).

- `cp (copy)` - Used to copy files and directories from one location to another.

  <ins>Basic Syntax</ins>

  ```
  cp [options] source destination
  ```
  - `source` : The file or directory you want to copy.
  - `destination` : The location where you want to copy the file or directory.

  <ins>Common Options</ins>

  - `-r` or `-R` : Recursively copy directories and their contents, no matter how deeply nested the subdirectories are.
  - `-i` : Prompt before overwriting files.
  - `-v` : Verbose mode, showing files as they are copied.
  - `-u` : Only copy files that are newer than the destination file or that don't exist at the destination.
  - `-n` : Do not overwrite existing files.

  Examples:

  1. Copy a single file:

  ```
  cp file.txt /path/to/destination/
  ```
  This copies file.txt to the specified destination directory.

  2. Copy multiple files:

  ```
  cp file1.txt file2.txt /path/to/destination/
  ```
  This copies both file1.txt and file2.txt to the destination.

  3. Copy a directory and its contents:

  ```
  cp -r /path/to/source_directory /path/to/destination_directory
  ```
  This recursively copies source_directory and all its contents to destination_directory.

  4. Copy with a prompt before overwriting:
  ```
  cp -i file.txt /path/to/destination/
  ```
  This prompts you to confirm before overwriting a file at the destination.

  5. Copy with verbose output:
  ```
  cp -v file.txt /path/to/destination/
  ```
  This shows the file names as they are being copied.

- `read` - Used to read a line of input from the user or from a file and assign it to a variable.

  Example:

  ```
  echo "Please enter your name:"
  read name
  echo "Hello, $name!"
  ```

  <ins>Additional Options</ins>

  - `-p` : Prompt the user with a message.
  ```
  read -p "Enter your age: " age
  echo "You are $age years old."
  ```
  - `-s` : Read input silently (e.g., for passwords).
  ```
  read -s -p "Enter your password: " password
  echo "Password entered."
  ```
  - `-a` : Store input in an array.
  ```
  read -a colors
  echo "First color: ${colors[0]}"
  ```

  - `-n` : Read a specified number of characters.
  ```
  read -n 1 -p "Press any key to continue..."
  ```

  - `-t` : Set a timeout for input.
  ```
  read -t 5 -p "Enter your name within 5 seconds: " name
  ```
  - `-r` : Prevent backslashes from being interpreted as escape characters.
  ```
  read -r name
  ```

  Example: Reading from a File

  Suppose you have a file named names.txt with the following content:
  ```
  Alice
  Bob
  Charlie
  ```

  You can use the read command in a Bash script to read each line of this file and process it. Here's how:
  ```
  #!/bin/bash
  
  # Open the file for reading
  while IFS= read -r line; do
      echo "Hello, $line!"
  done < names.txt
  ```

  Output

  When you run this script, the output will be:
  ```
  Hello, Alice!
  Hello, Bob!
  Hello, Charlie!
  ```
  This script reads each line of names.txt and processes it one by one.

- `grep` - Used for searching text within files or the output of other commands. It searches for lines that contain a specified pattern and displays those lines.

  <ins>Basic Syntax</ins>
  ```
  grep [options] pattern [file...]
  ```

  - `pattern` : The string or regular expression you're searching for.
  - `file` : The file or files in which to search. If no file is specified, grep searches the input provided via a pipe or standard input.

  <ins>Common Use Cases</ins>
  1. Search for a Simple String in a File:
  ```
  grep "hello" file.txt
  ```
  This searches for lines containing the string "hello" in file.txt and prints those lines.

  2. Search Across Multiple Files:
  ```
  grep "error" *.log
  ```
  This searches for the string "error" in all .log files in the current directory.

  3. Case-Insensitive Search
  ```
  grep -i "hello" file.txt
  ```
  The `-i` option makes the search case-insensitive, so it will match "hello", "Hello", "HELLO", etc.

  4. Display Line Numbers:
  ```
  grep -n "hello" file.txt
  ```
  The `-n` option displays the line numbers alongside the matching lines.

  5. Search for a Whole Word:
  ```
  grep -w "hello" file.txt
  ```
  The `-w` option ensures that only whole words matching "hello" are returned, so "hello" would match, but "helloworld" would not.

  6. Search Recursively in a Directory:
  ```
  grep -r "hello" /path/to/directory
  ```
  The `-r` option allows grep to search recursively through all files in the specified directory.

  <ins>Example in Piping</ins>

  You can use `grep` to filter the output of another command:
  ```
  ps aux | grep "bash"
  ```
  This command lists all running processes (`ps aux`) and then filters the output to show only those containing "bash".

  <ins>Regular Expressions</ins>
  
  `grep` can also use regular expressions for more complex searches:
  ```
  grep "^hello" file.txt
  ```
  This matches lines in `file.txt` that start with "hello".

## Bash Variables
  <ins>Declaring Variables</ins>

  Examples:
  ```
  NAME=Julian
  GREETING="Hello World!"
  AGE=25
  CURRENT_DATE=$(date)
  ```

  <ins>Accessing a Variable</ins>

  To use the value stored in a variable, you need to prefix the variable name with a $:
  ```
  echo $GREETING
  ```
  This will output:
  ```
  Hello World!
  ```

  <ins>Modifying Variables</ins>

  You can modify vairbales by reassigning values:
  ```
  AGE=25
  AGE=$((AGE + 1))
  echo $AGE # Outputs 26
  ```

## Bash Positional Arguments
  In Bash scripting, positional arguments are used to pass parameters or arguments to a script. These arguments are accessed within the script using special variables. Here’s how they work:
  
  - `$0` : The name of the script itself.
  - `$1`, `$2`, `$3`, ..., `$n` : The first, second, third, ..., nth arguments passed to the script.
  - `$#` : The total number of arguments passed to the script.
  - `$@` : All the arguments passed to the script, each as a separate word.
  - `$*` : All the arguments passed to the script as a single word.

  <ins>Example Script</ins>
  ```
  #!/bin/bash

  echo "Script Name: $0"
  echo "First argument: $1"
  echo "Second argument: $2"
  echo "All arguments (\$@): $@"
  echo "All arguments as a single string (\$*): $*"
  echo "Number of arguments: $#"
  ```

  <ins>Usage</ins>\
  If you save the script as example.sh and run it like this:
  ```
  ./example.sh arg1 arg2 arg3
  ```

  The output will be:
  ```
  Script Name: ./example.sh
  First argument: arg1
  Second argument: arg2
  All arguments ($@): arg1 arg2 arg3
  All arguments as a single string ($*): arg1 arg2 arg3
  Number of arguments: 3
  ```

  Positional arguments allow you to create flexible and dynamic scripts that can handle different inputs.

## Piping in Bash
  Piping in Bash is a powerful feature that allows you to take the output of one command and use it as the input to another command. This is done using the pipe operator (`|`).

  <ins>Basic Example</ins>
  ```
  command1 | command2
  ```

  - `command1` is executed first, and its output is passed directly as input to `command2`.
  - `command2` then processes the input it receives from `command1`.

  <ins>Practical Example</ins>\
  Suppose you want to list all files in a directory and then search for files with a specific word in their names:
  ```
  ls | grep "word"
  ```

  - `ls` lists all files in the current directory.
  - `grep "word"` filters the list, showing only the files that contain "word" in their names.

  <ins>Chaining Multiple Commands</ins>\
  You can chain multiple commands together:
  ```
  cat file.txt | grep "pattern" | sort
  ```

  - `cat file.txt` outputs the content of file.txt.
  - `grep "pattern"` filters lines containing "pattern".
  - `sort` sorts the filtered lines.

  Piping is essential for combining commands in Bash to create more complex and powerful workflows.
  
## Basic Vim Commands
- Opening a file:
  ```
  vim filename.sh
  ```
- Entering Insert Mode:
  - Press `i` to start inserting text into the file
- Saving and Exiting:
  - Press `Esc` to exit Insert Mode, then type `:wq` and press Enter to write to the file (save) and exit.
- Quitting Without Saving:
  - Press `Esc` and type `:q!` to quit without saving.
- Entering Append Mode:
  - Press `a` to start appending text into the file
    
