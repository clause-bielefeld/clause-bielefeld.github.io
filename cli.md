---
layout: post
title: Teaching / Command Line
permalink: teaching/cli/
---

# Using the (Unix) Command Line

## Prompts and Commands


If you open up your command line interpreter (e.g. some kind of terminal on Linux/MacOS, or Cygwin on Windows), you are greeted with the "command prompt". This indicates that the interpreter is ready to accept commands.

The prompt will look roughly like this:
- `user@host: WorkingDirectory$`

Here you can find the following information:
  - user: user name
  - host: name of the computer the user is currently logged in
  - WorkingDirectory: directory the command line interpreter is currently in
      - `~` designates the home directory: `/home/UserName`

Note: If using Cygwin on Windows, the root directory is the directory where Cygwin is installed (e.g. `C:\cygwin64`; which would make `C:\cygwin64\home\UserName` the home directory). Therefore, if you want to access a file with Cygwin, you have to save it to the Cygwin root directory or any subdirectory. In most cases, it is best to save the files somewhere in your home directory.

Commands in the Unix command line have the following format:
- `commandName [options] arguments`

The individual components are:
- commandName: name of a command to be executed in the command line
  - e.g. `ls` or `cd`
- Options: Additional (optional) settings for executing a command ("how you want to process something")
  - e.g. `uniq -c` for running `uniq` (merge lines / finding unique lines) with the additional `c` option (count the number of instances for every line)
    - you can add multiple options for a single command
- Arguments: Pieces of information provided to the command
  - e.g. file names: `cat file.txt` for running the command `cat` with the argument `file.txt` (i.e. using the `cat` command to read `file.txt`)

The kind of options and parameters you can (or have to) set depend on the respective command. Most commands have a `--help` option, which outputs a brief documentation about how the respective command can be used:
  - e.g. `ls --help` calls the documentation for the `ls` command

## Commands
- `ls` : list files and subdirectories in the current directory
- `mkdir` : create a new directory
  - `mkdir MyDocuments` : create the directory "MyDocuments" within the current working directory
- `cd` : change directory
  - `cd ..` : move to parent directory
  - `cd Documents` : move to subdirectory "Documents"
  - `cd ~` : move to home directory
- `cat` : read a text file
- `tr` : translate (groups of) characters to other (groups of) characters
- `sort` : sort lines (alphabetically, numerically)
- `uniq` : filter out repeated lines in a file
- `wc`: count words, lines and bytes

## Outputs

Many commands (e.g. `cat`, `ls`, `tr`, ...) result in some kind of output which is shown in the command line (e.g. the files and subdirectories in the current directory when `ls` is executed). This output can be redirected in two ways: a) it can be written in a text file instead of being displayed in the command line, or b) it can be passed on directly to a subsequent command.
  - To write the output to a file: add `> filename.txt` after the command
    - e.g. `ls > filesInThisDir.txt`: Executes `ls` and writes the output to the text file `filesInThisDir.txt`.
    - Note: This creates a new file. If a file with this name exists in the current directory, it is replaced with the newly created file.
    - Note: If the output is redirected to a file, there will be no output on the command line!
  - To pass the output to a subsequent command: add `| nextCommand` after the command
    - `|` is the "pipe" operator
    - e.g. `cat textfile.txt | wc`: reads `textfile.txt` with `cat`; passes the output from `cat` to `wc` (to count e.g. words)
    - the pipe operator can be used to chain multiple commands, with each command getting taking the output from the previous command as input. This allows for more complex ways of processing
      - e.g.:
      `cat textfile.txt | tr ' ' '\n' | sort` (reading a text file, splitting the text into individual words, and sort those words alphabetically)

## Further Resources

There are lots of further (and more detailed) resources about using the command line.
There are both tutorials, e.g. [this one](https://ubuntu.com/tutorials/command-line-for-beginners#1-overview), and collections for commands, e.g. [this one](https://www.codecademy.com/articles/command-line-commands).
