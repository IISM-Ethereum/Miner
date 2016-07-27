# Miner 



## How to connect 

    sudo apt install openssh-client

    ssh iism@172.22.73.230

PW ist in drobox ;-) 

## Access running Miner Instance

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

## Usage as Web-Server 

## Todo

prozessse via ssh starten und im Hintergrund ablaufen lassen

nodejs & nodemon installieren 

git installieren
