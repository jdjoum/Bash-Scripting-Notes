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

- `$?` - A special variable that holds the exit status of the most recently executed command. It's a valuable tool for checking if commands completed successfully or encountered errors.

  Exit Status Values:

  - 0: The command executed successfully.
  - 1: A generic error occurred.
  - 2-127: Specific error codes defined by the command itself.
  - 127: The command was not found.
  - 128+: The command terminated due to a signal.

  Example Usage:
  ```
  # Check if a command executed successfully
  if [ $? -eq 0 ]; then
    echo "Command executed successfully"
  else
    echo "Command encountered an error"
  fi
  ```

  By understanding and utilizing $?, you can write more robust and informative Bash scripts that handle errors gracefully and provide appropriate feedback to the user.

- `${1,,}` - Used for lowercasing the value of the first positional parameter ($1). Here's a breakdown:
  
  - `$1` refers to the first argument passed to the script or function.
  - `,,` is a parameter expansion operator that converts the value to lowercase.

  Example:

  ```
  #!/bin/bash
  echo "${1,,}"
  ```

  If you run this script with the argument "HELLO", it will output:
  ```
  hello
  ```

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

## Bash Output/Input Redirection
  Output redirection in Bash is a feature that allows you to control where the output of a command goes. Instead of displaying the output on the screen (standard output), you can redirect it to a file, another command, or even nowhere at all. Here are some common ways to use output redirection:

  1. Redirect Standard Output to a File
  ```
  command > file.txt
  ```
  This will redirect the output of `command` to `file.txt`. If `file.txt` already exists, it will be overwritten.

  2. Append Standard Output to a File
  ```
  command >> file.txt
  ```
  This appends the output of `command` to the end of `file.txt` without overwriting the existing content.

  3. Redirect Standard Error to a File
  ```
  command 2> error.txt
  ```
  This redirects the error messages (standard error) of `command` to `error.txt`.

  4. Redirect Both Standard Output and Standard Error to a File
  ```
  command > output.txt 2>&1
  ```
  This sends both standard output and standard error to `output.txt`.

  5. Redirect Output to /dev/null (Discard Output)
  ```
  command > /dev/null 2>&1
  ```
  This discards all output from the command, effectively silencing it.

  6. Redirect Input from a File
  ```
  command < input.txt
  ```
  This uses `input.txt` as the input for `command`.

  7. Combine Input and Output Redirection
  ```
  command < input.txt > output.txt
  ```
  This takes input from `input.txt` and sends output to `output.txt`.

  These are the basic techniques for output redirection in Bash. They can be combined and used in more complex scripts to manage input and output effectively.

  In Bash, `2>` and `2>&1` are used for redirecting standard error (stderr).

  <ins>How They Work Together</ins>

  - `2>` by itself directs stderr to a file or location you specify.
  - `2>&1` combines stderr with stdout, meaning both types of output will go to the same place, whether it's a file or another command.

## Test Operators in Bash
  Bash provides a powerful set of test operators to evaluate conditions and make decisions within your scripts. These operators allow you to compare values, check file attributes, and perform logical operations.

  <ins>Basic Comparison Operators</ins>

  - Equality:
    - `=` : Equal to (e.g., `if [ "$a" = "$b" ]; then...`)
    - `!=` : Not equal to (e.g., `if [ "$a" != "$b" ]; then...`)
  - Numerical Comparison:
    - `-eq` : Equal to numerically (e.g., `if [ "$a" -eq "$b" ]; then...`)
    - `-ne` : Not equal to numerically (e.g., `if [ "$a" -ne "$b" ]; then...`)
    - `-lt` : Less than numerically (e.g., `if [ "$a" -lt "$b" ]; then...`)
    - `-le` : Less than or equal to numerically (e.g., `if [ "$a" -le "$b" ]; then...`)
    - `-gt` : Greater than numerically (e.g., `if [ "$a" -gt "$b" ]; then...`)
    - `-ge` : Greater than or equal to numerically (e.g., `if [ "$a" -ge "$b" ]; then...`)
  - String Comparison:
    - `-eq` : Equal to (same as `=` for strings)
    - `-ne` : Not equal to (same as `!=` for strings)
    - `-lt` : Less than alphabetically (e.g., `if [ "$a" -lt "$b" ]; then...`)
    - `-le` : Less than or equal to alphabetically (e.g., `if [ "$a" -le "$b" ]; then...`)
    - `-gt` : Greater than alphabetically (e.g., `if [ "$a" -gt "$b" ]; then...`)
    - `-ge` : Greater than or equal to alphabetically (e.g., `if [ "$a" -ge "$b" ]; then...`)

  <ins>File Test Operators</ins>

  - File Existence:
    - `-e` : File exists (e.g., `if [ -e "$file" ]; then...`)
  - File Type:
    - `-f` : Regular file (e.g., `if [ -f "$file" ]; then...`)
    - `-d` : Directory (e.g., `if [ -d "$dir" ]; then...`)
    - `-l` : Symbolic link (e.g., `if [ -l "$link" ]; then...`)
    - `-p` : Named pipe (e.g., `if [ -p "$pipe" ]; then...`)
    - `-S` : Socket (e.g., `if [ -S "$socket" ]; then...`)
  - File Permissions: 
    - `-r` : Readable (e.g., `if [ -r "$file" ]; then...`)
    - `-w` : Writable (e.g., `if [ -w "$file" ]; then...`)
    - `-x` : Executable (e.g., `if [ -x "$file" ]; then...`)
  - File Attributes:
    `-s` : Non-zero size (e.g., `if [ -s "$file" ]; then...`)
    `-t` : Associated with a terminal (e.g., `if [ -t 1 ]; then...`)
  
  <ins>Logical Operators</ins>

  - And: `&&` (e.g., `if [ -f "$file" ] && [ -r "$file" ]; then...`)
  - Or: `||` (e.g., `if [ -f "$file" ] || [ -d "$dir" ]; then...`)
  - Not: `!` (e.g., `if ! [ -e "$file" ]; then...`)

  <ins>Example Usage</ins>

  ```
  if [ "$user" = "root" ]; then
    echo "You are the root user."
  fi

  if [ "$num" -gt 10 ]; then
      echo "$num is greater than 10."
  fi

  if [ -f "$file" ]; then
      echo "$file is a regular file."
  fi

  if [ -r "$file" ] && [ -w "$file" ]; then
      echo "$file is readable and writable."
  fi
  ```

  By effectively using these test operators, you can create powerful and flexible Bash scripts to automate tasks and make informed decisions based on various conditions.

## Conditionals in Bash
  In Bash scripting, conditionals are used to execute different commands based on certain conditions. The most common conditional statements are `if`, `else`, `elif`, and case. Here's a quick overview:

  1. If-Else Statements

  These are used to test conditions and execute commands accordingly.
  ```
  if [ condition ]; then
    # Commands to execute if the condition is true
  elif [ another_condition ]; then
    # Commands to execute if the second condition is true
  else
    # Commands to execute if none of the conditions are true
  fi
  ```
  - `[ condition ]` checks a condition (like comparing numbers, strings, or checking file existence).
  - `then` follows the condition, and the commands to execute if it's true are placed beneath.
  - `elif` is used for additional conditions.
  - `else` is the fallback if none of the conditions are true.

  Example:
  ```
  #!/bin/bash
  x=10

  if [ $x -gt 5 ]; then
    echo "x is greater than 5"
  elif [ $x -eq 5 ]; then
    echo "x equals 5"
  else
    echo "x is less than 5"
  fi
  ```

  2. Case Statement

  This is similar to switch in other programming languages, used for matching one value against multiple patterns.
  ```
  case expression in
    pattern1)
      # Commands for pattern1
      ;;
    pattern2)
      # Commands for pattern2
      ;;
    *)
      # Default commands if no pattern matches
      ;;
  esac
  ```
  Example:
  ```
  #!/bin/bash
  fruit="apple"

  case $fruit in
    "apple")
      echo "You selected apple"
      ;;
    "banana")
      echo "You selected banana"
      ;;
    *)
      echo "Unknown fruit"
      ;;
  esac
  ```
  In Bash, `esac` is used to close a `case` statement. It is simply "case" spelled backward, and it marks the end of the case block. Just like `fi` is used to close an `if` statement, `esac` is required to indicate the end of the `case` logic.

## Arrays and For Loops in Bash
  In Bash, arrays are a type of data structure that can store multiple values. Bash supports both indexed arrays and associative arrays.

  <ins>Indexed Arrays</ins>

  Indexed arrays are like standard arrays in other languages, where elements are accessed by their index.

  Creating an Indexed Array
  ```
  # Method 1: Declare and assign values
  my_array=(apple banana cherry)

  # Method 2: Declare and add elements later
  declare -a my_array
  my_array[0]="apple"
  my_array[1]="banana"
  my_array[2]="cherry"
  ```

  Accessing Elements
  ```
  echo ${my_array[0]}  # Output: apple
  ```

  Accessing All Elements
  ```
  echo ${my_array[@]}  # Output: apple banana cherry
  ```

  Length of Array
  ```
  echo ${#my_array[@]}  # Output: 3
  ```

  <ins>Associative Arrays</ins>

  Associative arrays allow you to use strings as keys.

  Creating an Associative Array
  ```
  declare -A fruits
  fruits[apple]="red"
  fruits[banana]="yellow"
  ```

  Accessing Elements
  ```
  echo ${fruits[apple]}  # Output: red
  ```

  Accessing All Keys
  ```
  echo ${!fruits[@]}  # Output: apple banana
  ```

  Accessing All Values
  ```
  echo ${fruits[@]}  # Output: red yellow
  ```

  Looping Through Arrays
  ```
  # Indexed array
  for element in "${my_array[@]}"; do
      echo $element
  done

  # Associative array
  for key in "${!fruits[@]}"; do
      echo "$key is ${fruits[$key]}"
  done
  ```

## Functions in Bash
  In Bash, a function is a reusable block of code that can be executed multiple times within a script. Functions allow you to break down complex scripts into simpler, manageable parts.

  Basic Syntax of a Bash Function:
  ```
  function_name(){
    # Code to execute
  }
  ```

  Example:
  ```
  greet() {
    echo "Hello, $1!"
  }

  # Calling the function with an argument
  greet "John"
  ```
  In this example, the function `greet` takes one argument (`$1`) and prints a greeting message.

  Key Points:

  - Arguments: Passed similar to how you pass arguments to a script. `$1`, `$2`, etc., represent the first, second, and so on arguments.
  - Return Values/Exit Codes: Functions don't return values like in some other languages but you can use `return` to exit a function with a status code:
  ```
  my_function() {
    if [ "$1" -gt 0 ]; then
        return 0  # success
    else
        return 1  # failure
    fi
  }
  ```
  - Using Function Output: You can capture the output of a function using command substitution:
  ```
  my_function() {
    echo "This is the result"
  }

  result=$(my_function)
  echo "Result: $result"
  ```
  Functions are a powerful feature in Bash for structuring your scripts effectively!

## Local Variables in Bash
  In Bash, local variables are variables that are only accessible within the function they are defined in. This is useful for preventing variable name conflicts between different parts of your script.

  Defining Local Variables

  To declare a local variable inside a function, use the local keyword:
  ```
  my_function() {
    local my_var="Hello, World!"
    echo "$my_var"
  }

  my_function
  # my_var is not accessible here
  ```

  Key Points:
  - Scope: Local variables are only available within the function in which they are declared. Outside the function, they are not accessible.
  - Default behavior: Without the `local` keyword, variables in Bash are global by default, meaning they can be accessed and modified outside the function.

  Example:
  ```
  my_function() {
    local name="John"
    echo "Inside function: $name"
  }

  my_function
  echo "Outside function: $name"  # Will not print anything because $name is local
  ```
  In this example, `name` is local to `my_function`, so it won't affect or be accessible outside the function.

  Use Case:

  Local variables are especially useful when writing larger scripts where multiple functions might use the same variable names. By declaring variables as local, you prevent unintended interference between different parts of your script.

## AWK in Bash
  `awk` is a powerful text processing tool in bash that's used to manipulate and analyze text files or streams. It allows for pattern matching and applying specific actions to lines in a file or input. Here’s a brief overview of its usage:

  Basic Syntax

  ```
  awk 'pattern { action }' file
  ```
  - pattern: What to search for in each line (optional).
  - action: What to do when the pattern is found (optional).
  - file: The file to process.
  
  If no action is specified, `awk` prints the matching lines by default.

  Common Examples
  
  1. Print entire file:
  ```
  awk '{ print }' filename
  ```

  2. Print specific columns (e.g. the second column):
  ```
  awk '{ print $2 }' filename
  ```

  3. Print lines that match a pattern:
  ```
  awk '/pattern/ { print }' filename
  ```

  4. Perform arithmetic operations:
  ```
  awk '{ print $1, $2, $1 + $2 }' filename
  ```

  5. Using field delimiters (e.g., comma-separated values):
  ```
  awk -F',' '{ print $1, $3 }' filename
  ```

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
    
