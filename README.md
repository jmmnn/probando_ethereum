# These are some notes on experiments with Ethereum

## Creating my own private Ethereum network (1 node)

Based on instructions from [here:](https://medium.com/@andresilva/step-by-step-guide-to-deploy-your-first-ethereum-contract-in-a-private-network-4dd9d333f112)
and [here:](https://medium.com/@idhww/simple-process-to-issue-a-token-on-ethereum-blockchain-520faaa229d9)  

All below works well on OSX. First you need to install Geth, then read on:

This generates a persistent Ethereum chain in your machine. Use this anytime to restart your node:  
```
$geth --dev --datadir ~/EthereumTestNet        
```

#in another terminal start the JS console. You can use this to connect your running private Ethereum chain.
```
  $geth --dev attach ipc:/Users/jmmnn1/EthereumTestNet/geth.ipc

  $personal.newAccount(“password”)
```
The new account is a hash, say: 0x10c4c1226cd2a7614e30146d4aa9a17adc090408
#create a second account

```
$personal.newAccount(“#password”)
```

#asssign name to new accounts
```
a = personal.listAccounts[0]
b = personal.listAccounts[1]
```

#get balance for each account
```
eth.getBalance(a)
eth.getBalance(b)
```

#start mining  #after some mining you automatically notice your balance grow:
```
$miner.start()
```

#verify that blocks are being created
```
$eth.blockNumber
```

#unlock an account
```
$personal.unlockAccount(a)
```

#send some ether
```
var txtReceipt = eth.sendTransaction({from:a, to:b, value:1})
```

#view details of the transaction
```
$eth.getTransactionReceipt(txtReceipt)
```

#confirm b has 1 ether
```
$ eth.getBalance(b)
```

#how to get info about my node:
```
$ admin.nodeInfo
```

#start your RPC server. It should be avakable at http://localhost:8545/
```
$ admin.startRPC()
``` 
