# Basics

## Using STDIN, STDOUT, STDERR....

STDIN is where commands are typed.

STDOUT is where commands send their results by default. You may be used to this, if having using commands like `cat` in the terminal.

STDERR is where commands send error messages by default.

STDOUT is the default for keyboards and most programs.

As a shell user, you can redefine what to use as STDIN, STDOUT, or STDERR by using redirection.

Redirection allows you to send STDOUT and STDERR to a file, and obtain STDIN.

`ls > NAME` is used for output redirection, the greater than. If you don't want to overwrite, you can use `>>`. You can also redirect things to a file. You'd use `grep` if you want to print stuff.

You can open the root shell by running `sudo -i`. You can run `ps aux` to get all of your processes. When navigating into a process via `/proc/`, `fd` is the file descriptor.

Pipes are like utilities when running commands. `| less` pipe for example only outputs what you can see on the screen. `| grep INPUT` allows you to print stuff that only contains the input you gave it.

## Internal commands

Internal commands are faster than external commands. They are a part of the bash binary. They don't need to be fetched from the disk compared to external commands, hence they are much faster.

## Variables

To set a variable `key=value`. `export key=value` to define a variable for not only the current shell, but all the subshells as well. You can refer to a variable using `echo $key`. If you want to print the variable with something else on it, then use `echo ${key}more-value-here-to-print`.

## Alias

Alias is a Bash internal command that allows you to define your own commands, good when you don't want to repeat yourself, especially when it comes to longer commands. `unalias name` to remove it.

## Startup files

Bash startup files are used to provide default settings for the operating system environment.

## Alternative shells

There are other shells out there, but bash remains the default, and is easy to run even if you're in a different shell.

## Exit codes

After execution, a command generates an exit code. With `echo $?` the last exit code can be requested. 0 means successful, 1 means generic error and anything else means there was an issue running the command. You can generate an exit code in your script by doing `exit n`.

# Shell scripts in a DevOps Environment

## What is a shell script?

A computer program designed to run in a shell, can be written in different scripting languages. They are easy to develop and a part of the default working environment.

## What is DevOps?

A set of practices that combines software development with IT operations to shorten the development lifecycle.

# Writing scripts

First make your script executable by running `chmod +x {script-file-name}`. Then you can run your script by pointing to the file name `./{filename}`, you can also call bash before it if you want.
