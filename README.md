<h1 align ="center">simple_shell</h1><br>

------------
Simple_Shell (Diet_Shell)
By Nelson Otieno <nellchieng@gmail.com> and Rophi Chukwu <chukwurophi@gmail.com>


## Repository Description

This repository contains the files to simulate a basic **Unix Shell** with its respective commands. It uses the POSIX API to implement many of the same functionalities of the first Ken Thompson's Shell.

The predominantly used calls are **read**, **write**, **open**, **execve**, **exit**, **fflush**, **fork**, **free**, **malloc**, **getline**, **isatty**, **perror**, **strtok**, **wait**, and **waitpid**.

This simple shell is a Shell interface written in C programming language that gives to the user a prompt * ($) *, after it accepts, it executes a user inputted command in a separate process called child process.

## This shell provides the following features:

* This program displays a prompt and waits that the user types a command. A command line always ends with a new line (when user push *ENTER* key).
* The prompt is displayed again each time a command has been executed.
* When the user enters exit, * Simple Shell * will end and returns the status 0.
* When the user enters exit *[status]*, *Simple Shell* will end and returns the inputted status, where *status* is a value from 0 to 255. 
* The user could stop the program using *Ctrl+D* (end of file).
* The shell handles the command lines with arguments and pathways.
* The program does not quit when the user imputs ^C (Ctrl+C).
* The program prints the current enviroment when the user types *env*.
* This program executes the most common shell commands as *ls*, *grep*, *find*, *pwd*, *rm*, *cp*, *mv*, *exit*, *env*, *history*, etc... with arguments.
* If an executable cannot be found, It prints an error message and displays the prompt again.
* This Shell supports commentaries using *#* 
* The *Simple Shell* does NOT support wildcard characters such as ls \*.dat in parameters (or commands).
* This shell does NOT support pipes *|*, shell logical operators as *&& or ||*, neither commands separator *;*.

## Process Description

The next steps are a brief description about how the shell works:

1. First, the parent process is created when the user run the program.
2. Then, the *isatty()* function using *STDIN_FILENO* file descriptor -fd- to tests if there is an open file descriptor referring to a terminal. If *isatty()* returns 1, the prompt is showed using *write()* with *STDOUT_FILENO* as fd and waits for an input user command line.
3. When the user types a command, *getline()* function reads an entire line from the stream and *strtok()* function breaks the inputted command into a sequence of non-empty tokens.
4. Next, it creates a separate child process suing *fork()* that performs the inputted command. Unless otherwise is specified, the parent process waits for the child to exit before continuing.
5. After tokening the command, *execve()* function brings and executes it, the it frees all allocated memory with *free()*.
6. Finally, the program returns to main process: prints the prompt, and waits for another user input.


## Authors:

- *Nelson Otieno* - [@boxtobox-nelly21](https://github.com/boxtobox-nelly21)
- *Rophi Chukwu*  - [@beginners-lock](https://github.com/beginners-lock)
