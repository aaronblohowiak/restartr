# restartr

retarter does two things: it launches a process, and it monitors files.  

when the files change, it `kill -9`'s the process and starts another one.

## Usage:
put it in your path.

`restarter "node server.js" **/*.js`

### Requirements
node in your $PATH (tested with 0.2.0)

### TODO:
Use Isaac's node_glob
