# Bash-Scripting-Notes
This repository contains notes and example scripts based on what I learned from the Free Code Camp [Bash Scripting Tutorial for Beginners](https://www.youtube.com/watch?v=tK9Oc6AEnR4&t=725s). It covers essential Bash scripting concepts, commands, and practical examples.

## Basic Bash Commands
- ls - Lists directory contents
- cd - Changes the current directory
- pwd - Prints the working directory
- echo - Displays text or the value of a variable in the terminal

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
- cat - Concatenates and displays the contents of files in the terminal
  
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
## Basic Vim Commands
- Opening a file:
  ```
  vim filename.sh
  ```
- Entering Insert Mode:
  - Press "i" to start inserting text into the file
- Saving and Exiting:
  - Press "Esc" to exit Insert Mode, then type ":wq" and press Enter to write to the file (save) and exit.
- Quitting Without Saving:
  - Press "Esc" and type ":q!" to quit without saving.
    
