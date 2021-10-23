# TD5--Baking-On-Tezos

## Cleaning up Setup 	:+1:
## Secure setup with SSH public key :+1:

## Install dependencies :speech_balloon:
Don't need

## Install Tezos client :cowboy_hat_face:
Install on Testnet => now is [Granadanet](https://granadanet.tzkt.io/)

Installation
```bash
$sudo add-apt-repository ppa:serokell/tezos && sudo apt-get update
$sudo apt-get install -y tezos-client
$sudo apt-get install -y tezos-node
$sudo apt-get install -y tezos-baker-010-ptgranad
$sudo apt-get install -y tezos-endorser-010-ptgranad
$sudo apt-get install -y tezos-accuser-010-ptgranad
$tezos-client –version
```

## Redeem testnet Tez on a Faucet :rofl:

- Create an account
Don't use this, it's Useless
```bash
$tezos-node identity generate
```
Should go on this [link](https://faucet.tzalpha.net/) to have an account

- Get Granadanet Faucet :sweat_smile:
Sometime you will get from your wallet, Or ...


## Run Tezos Client :ok_hand:
Find your Network [Here](https://tezos.gitlab.io/user/multinetwork.html)
- Get Configuration init file for Granadanet
```bash
$tezos-node config init --data-dir ~/tezos-granadanet --network granadanet
```
- Activate Account
```bash
$tezos-client activate account "#Username" with "#Faucet JSON FILE GENERATE BY TzAlpha"
$tezos-client get balance for "Username" #Check faucet
``` 
- Run Client Node
```bash
$tezos-node run --data-dir ~/tezos-granadanet --network granadanet --rpc-addr 127.0.0.1:8732 --connections 10
```


## Register an account as a Baker
Client to Delegate
```bash
$tezos-client register key "#UsernameClient" as delegate
```


## Run Tezos Baker :speech_balloon:
```bash
tezos-baker run with local node "/home/.tezos-node" "#Baker"
```


## Register a second account, and delegate baking rights to the first account :speech_balloon:
Follow this [link](https://opentezos.com/baking/delegating/)
```bash
$tezos-client set delegate for "#NewBaker" to "#Baker"
```

## Run Tezos Endorser :speech_balloon:
```bash
$tezos-endorser run "#Baker"
```

## Run Tezos Accuser :speech_balloon:
```bash
$tezos-accuser run
```

## Turn all 3 Softwares into Services :speech_balloon:
Use systemctl [enable,start,restart (if fail),status, stop(kill process) ]

## Documentation
[Tezos Gitlab p1](https://tezos.gitlab.io/index.html)
[Tezos Gitlab p2](https://gitlab.com/tezos/tezos)
[How To](https://gist.github.com/dakk/bdf6efe42ae920acc660b20080a506dd)






