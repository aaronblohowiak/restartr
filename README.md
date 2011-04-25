# How do I automatically restart my node server when files change?

If you are developing in Node.JS and you want to autoreload new versions of your files, use restartr! This actually works with any child process, but Node.Js development was the inspiration.

This only supports POSIX systems (Mac OSX, Linux, BSD, Solaris &etc.)  No MS Windows.

# restartr

retarter does two things: it launches a process, and it monitors files.  

when the files change, it kills the child process and restarts it.

## Usage:
put it in your path, then call it in a way that matches this pattern:

    restartr [program name] [arg1 sent to program] [files to watch ...]

Here is an example that uses bash expansion to save some keystrokes in listing the files to watch:

    restartr node server.js **/*.js

In this example, "node" is the command, and "server.js" is the argument to this command.

if you want to have 0-N args, use the explicit syntax:

    restartr -c [cmd] -a [arg1] -a [arg2] [file1] ... [fileN]

## Immediate crash detection

If the child process quits within 5 second, then wait for a file change to restart it. Otherwise, restart immediately.  You can override the definition of "immediately" by setting the ENV var `IMMEDIATE_CRASH_THRESHHOLD`

    IMMEDIATE_CRASH_THRESHHOLD=100 restartr [program name] [arg1 sent to program] [files to watch ...]

This will only wait to restart the program if it crashes in the first 100 ms.

## Install

`npm install restartr`

or, just download the one file and put it in your $PATH

## Fine print
### Requirements
node in your $PATH (tested with 0.2.0)

### Dependencies
installed automatically when using npm to install restartr

node-optimist 0.0.3

colors  0.5.0

### TODO:
Use Isaac's node_glob, or some other way to avoid shell expansion overrun.
Implement --quiet
Implement --ignore="regex" to ignore a files included that should be ignored