# Ethereum
Create a private testnet using geth on multiples computers

## Install Geth

sudo apt-get install software-properties-common
sudo add-apt-repository -y ppa:ethereum/ethereum
sudo apt-get update
sudo apt-get install ethereum

## Set up the genesis block common on the machines 

### If you want to know about each variable go to this link : https://ethereum.stackexchange.com/questions/2376/what-does-each-genesis-json-parameter-mean

{
  "alloc": {},
  "coinbase"   : "0x0000000000000000000000000000000000000000",
  "difficulty" : "0x20000",
  "extraData"  : "",
  "gasLimit"   : "0x2fefd8",
  "nonce"      : "0x0000000000000042",
  "mixhash"    : "0x0000000000000000000000000000000000000000000000000000000000000000",
  "parentHash" : "0x0000000000000000000000000000000000000000000000000000000000000000",
  "timestamp"  : "0x00"
}

### Running geth init on the fisrt machine and theses commands

$ geth --datadir="ethdata" init mygenesis.json

### Be sure to use the same network id

$ geth --datadir="ethdata" --networkid 65535 --nodiscover console

### When you are in the commands line just write this command

>>personal.newAccount("Your Password")

### setup the genesis block again on the instance using geth init. Launch geth console on the second geth computer. Ensure to provide the same networkid that you had provided in the first terminal. Once the geth console has started, you will need to execute the addPeer command in order to establish a handshake between the two nodes.

>>admin.addPeer("enode://90b7cbbaee94ab6e5bc7c5e8080bf8e2dfed5047b7c19ac61ee82511bef40faf9be2066258228ce7a71ab97b508dbef3c8f50fcf31dedfd43f2f0abd7f618db9@172.129.23.46:30303?discport=0")
true

### You will now notice that a handshake has been established between both the nodes. This can be cross verified using the command admin.peers, which would list all the nodes within the network.
### Commands such as net.peerCount will list the total number of peers within the ethereum network.






