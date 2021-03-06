# IISM - Private Blockchain

In order to disburden private computers from the the CPU-intensive mining process, we have installed a miner at the IISM institute. It is accessible via ssh and ought to be online 24/7.


## Pre-Requisite

Install a ssh client of your choice, i.e.:

    openssh-client (Linux)
    built-in MacOS
    Putty (Win)

## How to connect to the node

Establish vpn connection to KIT network and connect via

    ssh iism@172.22.73.230

PW will be distributed upon request.

## Access running Miner instance

    geth attach ipc:/home/iism/ETH/EthereumPrivate/geth.ipc
    
Note: Due to electricity costs and limited memory stop mining once nobody is working on the chain ;-) 
In order to check whether miner is currently running:

    eth.mining


## Access private chain 

    geth --datadir /home/USER/privateEthereum/ init /YourPathTo/Genesis.json
    geth --datadir /home/USER/privateEthereum/ --networkid 27 console
    
In order to get going initially you need to add so called bootstrap nodes (in our case it is our only miner): 

    admin.addPeer("enode://c831dab19841eed1d4fc925e8a5c8103309fec646750c45d4effb43a5c411da6b3f01280d7f1d4a8716989b556bfb3ad792ec0e8aaff74a7737bfd567f7e1d48@[172.22.73.230]:30307")

## Start Command for the Node 
```    
    geth --datadir "/home/USER/privateEthereum" init CustomGenesis.json
    geth --port 30303 --rpc --rpcaddr "172.22.73.230" --rpcport 8545 --rpccorsdomain "http://172.22.73.230:8081" --datadir "/home/iism/ETH/EthereumPrivate/" --networkid 27 console
```    
**Note**: rpcaddr "localhost" does not work for what ever reason ... 

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
## Connect Application to Blockchain from within vpn

    web3 = new Web3();
    web3.setProvider(new web3.providers.HttpProvider("http://172.22.73.230:8545"));
    web3.eth.defaultAccount = web3.eth.coinbase;

## Start remote processes via SSH

In order to start and keep a process running via SSH even after disconnecting, one can leverage the `screen` command as follows:

    ssh iism@172.22.73.230
    screen # starts a new screen session
    # start any process, such as mining, nodemon, etc.

Press `CTRL`+`a`, `d` to detach from the screen session and enter `exit` to exit the SSH session.

When you want to resume that session, just connect again and enter `screen -r` (or additionally `-d` in case you still have an open connection elsewhere).

## Remote Controle

list all processes: 

    ps x
   
kill process 

    kill -15 < pid-ID-number >

show all screens. (ssh terminals with autonomously running processes)

    screen -ls 

    
## Usage as Web-Server
1. Create Folder and pull remote repository via git

2. Create ssh terminal for nodejs server instance and run server. 
```
    ssh iism@172.22.73.230
    screen -S myNodeJsServer
    node MyServer.js 
```    
3. detach from the screen session: `CTRL`+`a`, `d`


## Todo on remote computer

install nodemon

install mist 

install vnc

exchange graphic card 

### Authors
Jonas-Taha El Sesiy (@elsesiy)

Magnus Gödde (@mgsgde)  

