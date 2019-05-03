# go-btfs

## What is BTFS?

BitTorrent File Sharing (BTFS) is a file-sharing protocol forked from 
IPFS that utilizes the TRON network for integration with DApps and smart 
contracts. In current smart-contract based networks like Ethereum and NEO, 
there exists no mechanism for large file transfer. BTFS allows for 
tokenized large file transfers. This paper presents a proposal for a BTFS 
and TRON based decentralized social media DApp which is censorship 
resistant and implements a tokenized reward system to content creators.


## Table of Contents

- [Install](#install)
  - [System Requirements](#system-requirements)
  - [Build from Source](#build-from-source)
    - [Install Go](#step1-install-go)
<<<<<<< HEAD
    - [Access To Private Repo](#step2-access-to-private-repo)
    - [Download Source Code](#step3-download-source-code)
    - [Build And Join BTFS Private Net](#step4-build-and-join-btfs-private-net)
    - [Run BTFS At The Backend](#step5-run-btfs-at-the-backend)
=======
    - [Download Source Code](#step2-download-source-code)
    - [Build And Join BTFS Private Net](#step3-build-and-join-btfs-private-net)
    - [Run BTFS At The Backend](#step4-run-btfs-at-the-backend)
>>>>>>> doc: add instruction for setup node on btfs private net.
- [Usage](#usage)
- [Getting Started](#getting-started)
  - [Some things to try](#some-things-to-try)
- [Packages](#packages)
- [License](#license)


## Install

### System Requirements

BTFS can run on most Linux, macOS, and Windows systems. We recommend 
running it on a machine with at least 2 GB of RAM (it’ll do fine with 
only one CPU core), but it should run fine with as little as 1 GB of 
RAM. On systems with less memory, it may not be completely stable.


### Build from Source

#### Step1 Install Go

The build process for btfs requires Go 1.11 or higher. If you don't 
have it: [Download Go 1.12+](https://golang.org/dl/). Or use the 
following command:
```
cd /tmp
GO_PACKAGE=go1.12.4.linux-amd64.tar.gz
wget https://golang.org/dl/$GO_PACKAGE
sudo tar -xvf $GO_PACKAGE
sudo mv go /usr/local
sudo rm $GO_PACKAGE
go version
```

You'll need to add Go's bin directories to your `$PATH` environment 
variable e.g., by adding these lines to your `/etc/profile` (for a 
system-wide installation) or `$HOME/.profile`:

```
export GOPATH=${HOME}/go
export PATH=$PATH:/usr/local/go/bin
export PATH=$PATH:$GOPATH/bin
export GO111MODULE=on
```

(If you run into trouble, see the [Go install instructions](https://golang.org/doc/install)).


#### Step2 Access To Private Repo
Firstly, you need your github token to access the private github repo. If you don't have a github token, following the guide [Generate github token](https://help.github.com/en/articles/creating-a-personal-access-token-for-the-command-line) to get your github token.

<<<<<<< HEAD
Put your github token to git config:
```
export GITHUB_TOKEN=(${Your github token})
git config --global url."https://${GITHUB_TOKEN}:x-oauth-basic@github.com/TRON-US".insteadOf "https://github.com/TRON-US"
=======
#### Step2 Download Source Code
```
$ git clone https://github.com/TRON-US/go-btfs.git
$ cd go-btfs
>>>>>>> doc: add instruction for setup node on btfs private net.
```

#### Step3 Build And Join BTFS Private Net

Your can choose to using on-step script to compile and build or just follow step by step.

<<<<<<< HEAD
#### Step3 Download Source Code

```
$ git clone https://github.com/TRON-US/go-btfs.git
$ cd go-btfs
```


#### Step4 Build And Join BTFS Private Net

Your can choose to using on-step script to compile and build or just follow step by step.

##### Using One-step Script

`bash install_btfs.sh`

##### Step-by-step Instruction

###### 1. Compile and build:
=======
##### Using One-step Script

`bash install_btfs.sh`

##### Step-by-step Instruction

###### 1. To access github private repo:
```
$ export GITHUB_TOKEN=9e2b088b6091e4452696aac6503f30d4c16c7c7c
$ git config --global url."https://${GITHUB_TOKEN}:x-oauth-basic@github.com/TRON-US".insteadOf "https://github.com/TRON-US"
```

###### 2. Compile and build:
>>>>>>> doc: add instruction for setup node on btfs private net.

```
$ make install
go version go1.12.4 linux/amd64
bin/check_go_version 1.12
go install -ldflags="-X "github.com/ipfs/go-ipfs".CurrentCommit=63ae486fa-dirty" ./cmd/btfs
```
If you are building on FreeBSD instead of `make install` use `gmake install`.

Show if btfs exec file has been created:
```
$which btfs
/home/ubuntu/go/bin/btfs
```
<<<<<<< HEAD
###### 2. Init a btfs node:
=======
###### 3. Init a btfs node:
>>>>>>> doc: add instruction for setup node on btfs private net.
```
$ btfs init
initializing BTFS node at /home/ubuntu/.btfs
generating 2048-bit RSA keypair...done
peer identity: QmTkQjKAtfh2GNDPmtnFB8d..................
to get started, enter:

        btfs cat /btfs/QmS4ustL54uo8FzR9455qaxZwuMi........H4uVv/readme
```


<<<<<<< HEAD
###### 3. Auto Update Setting
=======
###### 4. Auto Update Setting
>>>>>>> doc: add instruction for setup node on btfs private net.

Create a config.yaml file in the same path of your btfs binary path. The config.yaml file has the following context:
```
version: 0.0.4    # btfs version
md5: 034cf64b76f8bf5f506ce6aca9fa81c4    #btfs binary md5
autoupdateFlg: true     # is auto update
sleepTimeSeconds: 20        # how often to auto update (second）.
```


<<<<<<< HEAD
###### 4. Join BTFS Private Net
=======
###### 5. Join BTFS Private Net
>>>>>>> doc: add instruction for setup node on btfs private net.
Put the swarm.key in /.btfs, and then run the node. [Get swarm.key](https://github.com/TRON-US/go-btfs/blob/master/swarm.key)
```
$ mv swarm.key ~/.btfs/swarm.key
```
Remove ipfs bootstrap:
```
$ btfs bootstrap rm --all  (if there is error like this: Error: cannot 
connect to the api. Is the daemon running? To run as a standalone CLI 
command remove the api file in `$IPFS_PATH/api`, please run `nohup btfs 
daemon </dev/null > /dev/null 2>&1 &` and then run this command.)
```
Join the private net work:
```
$ btfs bootstrap add /ip4/3.18.120.107/tcp/4001/ipfs/QmcmRdAHQYTtpbs9Ud5rNx6WzHmU9WcYCrBneCSyKhMr7H
added /ip4/3.18.120.107/tcp/4001/ipfs/QmcmRdAHQYTtpbs9Ud5rNx6WzHmU9WcYCrBneCSyKhMr7H
```
Enable Cross-Origin Resource Sharing:
```
$ btfs config --json API.HTTPHeaders.Access-Control-Allow-Origin "[\"*\"]"
$ btfs config --json API.HTTPHeaders.Access-Control-Allow-Methods '["PUT", "GET", "POST", "OPTIONS"]'
$ btfs config --json API.HTTPHeaders.Access-Control-Allow-Credentials "[\"true\"]"
```
Enable gateway, api port:
```
$ btfs config Addresses.API /ip4/0.0.0.0/tcp/5001
$ btfs config Addresses.Gateway /ip4/0.0.0.0/tcp/8080
```

<<<<<<< HEAD
#### Step5 Run BTFS At The Backend
=======
#### Step4 Run BTFS At The Backend
>>>>>>> doc: add instruction for setup node on btfs private net.
```
you need to make sure there is no btfs node already running, using `ps -ef |grep "btfs daemon"` to check if there is btfs node running and then kill the node process if it is, then running the following command:
$ nohup btfs daemon </dev/null > /dev/null 2>&1 &
```
Check if your node is connect to BTFS private net:
```
$ btfs swarm peers
/ip4/3.18.120.107/tcp/4001/btfs/QmcmRdAHQYTtpbs9Ud5rNx6WzHmU9WcYCrBneCSyKhMr7H
```


## Usage

```
  btfs - Global p2p merkle-dag filesystem.

  btfs [--config=<config> | -c] [--debug | -D] [--help] [-h] [--api=<api>] [--offline] [--cid-base=<base>] [--upgrade-cidv0-in-output] [--encoding=<encoding> | --enc] [--timeout=<timeout>] <command> ...

SUBCOMMANDS
  BASIC COMMANDS
    init          Initialize btfs local configuration
    add <path>    Add a file to BTFS
    cat <ref>     Show BTFS object data
    get <ref>     Download BTFS objects
    ls <ref>      List links from an object
    refs <ref>    List hashes of links from an object
  
  DATA STRUCTURE COMMANDS
    block         Interact with raw blocks in the datastore
    object        Interact with raw dag nodes
    files         Interact with objects as if they were a unix filesystem
    dag           Interact with IPLD documents (experimental)
  
  ADVANCED COMMANDS
    daemon        Start a long-running daemon process
    mount         Mount an BTFS read-only mountpoint
    resolve       Resolve any type of name
    name          Publish and resolve IPNS names
    key           Create and list IPNS name keypairs
    dns           Resolve DNS links
    pin           Pin objects to local storage
    repo          Manipulate the BTFS repository
    stats         Various operational stats
    p2p           Libp2p stream mounting
    filestore     Manage the filestore (experimental)
  
  NETWORK COMMANDS
    id            Show info about BTFS peers
    bootstrap     Add or remove bootstrap peers
    swarm         Manage connections to the p2p network
    dht           Query the DHT for values or peers
    ping          Measure the latency of a connection
    diag          Print diagnostics
  
  TOOL COMMANDS
    config        Manage configuration
    version       Show btfs version information
    update        Download and apply go-ipfs updates
    commands      List all available commands
    cid           Convert and discover properties of CIDs
    log           Manage and show logs of running daemon
  
  Use 'btfs <command> --help' to learn more about each command.
  
  btfs uses a repository in the local file system. By default, the repo is
  located at ~/.btfs. To change the repo location, set the $BTFS_PATH
  environment variable:
  
    export BTFS_PATH=/path/to/btfsrepo
```


## Getting Started

To start using BTFS, you must first initialize BTFS's config files on your
system, this is done with `btfs init`. See `btfs init --help` for information on
the optional arguments it takes. After initialization is complete, you can use
`btfs mount`, `btfs add` and any of the other commands to explore!


### Some things to try

Basic proof of 'btfs working' locally:

	echo "hello world" > hello
	btfs add hello
	# This should output a hash string that looks something like:
	# QmT78zSuBmuS4z925WZfrqQ1qHaJ56DQaTfyMUF7F8ff5o
	btfs cat <that hash>


## Development

Some places to get you started on the codebase:

- Main file: [./cmd/btfs/main.go](https://github.com/TRON-US/go-btfs/blob/master/cmd/btfs/main.go)
- CLI Commands: [./core/commands/](https://github.com/TRON-US/go-btfs/tree/master/core/commands)
- libp2p
  - libp2p: [libp2p](https://github.com/libp2p/go-libp2p)
  - DHT: [DHT](https://github.com/libp2p/go-libp2p-kad-dht)
  - PubSub: [PubSub](https://github.com/libp2p/go-libp2p-pubsub)


### Testing

```
make test
```

### Development Dependencies

If you make changes to the protocol buffers, you will need to install the [protoc compiler](https://github.com/google/protobuf).


## License

[MIT](./LICENSE)


## TODO
### Troubleshooting