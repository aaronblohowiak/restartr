# restartr

retarter does two things: it launches a process, and it monitors files.  

when the files change, it `kill -9`'s the process and starts another one.

## Usage:
put it in your path.

`restarter node server.js **/*.js`

In this example, "node" is the command, and "server.js" is the argument to this command.

## Install

`npm install restartr`

or, just download the one file and put it in your $PATH

### Requirements
node in your $PATH (tested with 0.2.0)

### TODO:
Use Isaac's node_glob

Use an opt parser so you can pass more than one argument to command that you want to keep-alive.
