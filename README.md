# Miner



## Pre-Requisite

Install a ssh client of your choice, i.e.:

    openssh-client (Linux)
    built-in MacOS
    Putty (Win)

## How to connect to node

Establish vpn connection to KIT network and connect via

    ssh iism@172.22.73.230

PW will be distributed upon request.

## Access running Miner instance

    geth attach ipc:/home/iism/ETH/EthereumPrivate/geth.ipc

## Genesis.json

    {
    	"nonce": "0x6767676767",
    	"timestamp": "0x0",
    	"parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
    "extraData": "0x0",
    	"gasLimit": "0x800000000",
    	"difficulty": "0x400",
    	"mixhash": "0x0000000000000000000000000000000000000000000000000000000000000000",
    	"coinbase": "0x3333333333333333333333333333333333333333",
    	"alloc": {
       "0xd24901517c1a7ce6d6bbcc6bfd93b5547567cefb": {"balance":"1000000000000000000000000000000"}
    	}
    }

## Start remote processes via SSH

In order to start and keep a process running via SSH even after disconnecting, one can leverage the `screen` command as follows:

    ssh iism@172.22.73.230
    screen # starts a new screen session
    # start any process, such as mining, nodemon, etc.

Press `CTRL`+`a`, `d` to detach from the screen session and enter `exit` to exit the SSH session.

When you want to resume that session, just connect again and enter `screen -r` (or additionally `-d` in case you still have an open connection elsewhere).

## Usage as Web-Server

## Todo

nodejs & nodemon installieren

git installieren
