# How to start the network
Start node 1 in a terminal windows  
`./geth --datadir node1 --unlock "0x53714D0624Bc6066A6682BF4806968B721702E98" --mine --rpc --allow-insecure-unlock`  
Enter password: markyang  

Start node 2 in a separate terminal windows  
`./geth --datadir node2 --unlock "0xF83D8ec4E6cCf02C3f5d1d8504cd7d7B8dE67291" --mine --port 30304 --bootnodes "enode://1103801b71ae40bbe15d03470827d3e01f3131a404b6782c22bb3fa9e7f034228f0f0be3871fc4f76e7dca952868c4aa81d1c47aa6242808f999337cc722f536@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock`  
Enter password: markyang

# Explanation of the flags
`--datadir value`: Data directory for the databases and keystore (default: "~/.ethereum")

` --unlock value`: Comma separated list of accounts to unlock

The `--mine` flag tells the node to mine new blocks.

`--rpc` flag enables us to talk to the first node, which will allow us to use MyCrypto to transact on our chain.

`--allow-insecure-unlock` flag allows insecure account unlocking when account-related RPCs are exposed by http

Since the first node's sync port already took up 30303, we need to change this one to 30304 using `--port`

The `--bootnodes` flag allows you to pass the network info needed to find other nodes in the blockchain. This will allow us to connect both of our nodes.

In Microsoft Windows, we need to add the flag `--ipcdisable`. Due to the way Windows spawns new IPC/Unix sockets, it doesn't allow for having multiple sockets running from geth at once. Since we are only using RCP we can safely disable the IPC sockets.

# Configuration of the network
Chain ID: 888

Account password: markyang

Ports:  
Node 1 - 30303  
Node 1 - 30304

# How to send a transaction
- Open MyCrypto wallet 
- Set up a custom network 
  - Node Name: assignmentnet 
  - Network: Custom
  - Network Name: assignmentnet
  - Currency: ETH
  - Chain ID: 888
  - URL: http://127.0.0.1:8545
- Import the keystore file from the node1/keystore directory into MyCrypto (Password: markyang). This will import the private key.  
- Send a transaction from the node1 account (Address: 0x53714D0624Bc6066A6682BF4806968B721702E98) to the node2 account (Address: 0xF83D8ec4E6cCf02C3f5d1d8504cd7d7B8dE67291).
