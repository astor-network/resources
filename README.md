*Quick links*
[Website](http://astor.host)
[Block explorer](http://astor.tmio.io)

# Resources

This repository contains resources to participate in the [Astor testnet](https://astor.host).

# Run an Astor node

Astor's chain id is 212.

## Besu

```
docker run --name besu --network host hyperledger/besu:21.1.6 --rpc-http-enabled --rpc-http-api=admin,eth,debug,miner,net,txpool,priv,trace,web3 --network=astor --bootnodes=enode://b638fc3dca6181ae97fac2ea0157e8330f5ac8a20c0d4c63aa6f98dcbac4e35b4e023f656757b58c1da7a7b2be9ffad9342e0f769b8cf0f5e35ff73116ff7dfd@3.16.171.213:30303 --sync-mode=FULL
```

## Core-Geth

Coming soon! You can try with our patch:

```
$> git clone https://github.com/atoulme/Core-Geth
$> git checkout -b keccak_mining origin/keccak_mining
$> cd Core-Geth
$> make
$> ./build/bin/geth --astor --http.addr=0.0.0.0 --http.vhosts="*" --miner.etherbase="0x46652437Dc2F978952c5F5667533874c294E4E84" --http --mine
```

Feel free to replace the etherbase address with your own!

# Request funds

A faucet is available at http://astor.tmio.io:8080.

# Run a miner

Run Besu with its miner enabled:

```
docker run --name besu --network host hyperledger/besu:21.1.6 --rpc-http-enabled --rpc-http-api=admin,eth,debug,miner,net,txpool,priv,trace,web3 --network=astor --bootnodes=enode://b638fc3dca6181ae97fac2ea0157e8330f5ac8a20c0d4c63aa6f98dcbac4e35b4e023f656757b58c1da7a7b2be9ffad9342e0f769b8cf0f5e35ff73116ff7dfd@3.16.171.213:30303 --sync-mode=FULL --miner-enabled --miner-stratum-enabled --miner-coinbase=fe3b557e8fb62b89f4916b721be55ceb828dbd73 --miner-stratum-enabled --miner-stratum-host=0.0.0.0
```

You can run alongside a miner.

## CPU miner

The CPU miner is a Python script. It will likely not have a high enough hashrate to mint tokens on the network, but can be useful if you're just starting out.

```
docker run --name cpu-miner --network host tmio/keccak-cpu-miner:latest http://0.0.0.0:8545 -n 1000
```

## GPU miner

Head over to [the keccakminer repository for full instructions](https://github.com/epicblockchain/keccakminer).
