# go-blockchain
A basic blockchain implementation in Golang.

## Installation and Usage

### CLI Usage
We provide a command line tool to setup a blockchain on your machine.

The CLI is powered by [cobra](https://github.com/spf13/cobra), which is a library for creating powerful modern CLI applications as well as a program to generate applications and command files.

run `go run . -h` to get information about the cli.

Here is a sample output, it is not a stable version, we're still woking on it.
```
Gobc is a simplified blockchain implemented in Go

Usage:        
  gobc [flags]
  gobc [command]

Available Commands:
  address     Get the address of the given node
  completion  generate the autocompletion script for the specified shell
  connect     Connect a node to another
  help        Help about any command
  mine        start mining at the given node
  newnode     Create a new node with given port
  printchain  Print all the blocks of the blockchain
  send        Send a message from a node to another
  startnode   Start the node running on given port

Flags:
      --config string   config file (default is $HOME/.gobc.yaml)
  -h, --help            help for gobc

Use "gobc [command] --help" for more information about a command.
```

### How to Run
[NOTE] Run commands below under the project root.

1. create three nodes, run commands below in three terminals
```go
go run . newnode -p 3000
go run . newnode -p 3001
go run . newnode -p 3002
```

2. open a new terminal and run commands below to connect these nodes
```go
go run . connect -from localhost:3000 -to localhost:3001
go run . connect -from localhost:3001 -to localhost:3002
```

3. run `mine` with a `address` to trigger a node listening at the `address` to start mining, when a new block is created, the node should broadcast it to all its known peers.
```go
go run . mine -address localhost:3000
```