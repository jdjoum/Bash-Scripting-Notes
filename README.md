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
    
