## Tac-Network-node


## Installation

## 1.Update your system
```bash
sudo apt update && sudo apt upgrade -y
```

## 2.Install Go
```bash
curl -OL https://go.dev/dl/go1.21.0.linux-amd64.tar.gz
sudo rm -rf /usr/local/go
sudo tar -C /usr/local -xzf go1.21.0.linux-amd64.tar.gz
echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.bashrc
source ~/.bashrc
```

## 3.Install jq / Install curl
```bash
sudo apt install -y jq
sudo apt install -y curl
curl --version
```

## 4. Install tacchaind
```bash
git clone https://github.com/TacBuild/tacchain
cd tacchain
make install
```

## 5.Initialize Your Node
```bash
tacchaind init testnode --chain-id tacchain_2390-1 --home .testnet
```
- Edit your .testnet/config/config.toml
```bash
nano .testnet/config/config.toml
```

- Modify the Moniker name(write the node name)
- Copy this content on this file
```sh
# Set block time
timeout_commit = "3s"

# Add persistent peers
persistent_peers = "9b4995a048f930776ee5b799f201e9b00727ffcc@107.6.94.246:45120,e3c2479a6f418841bd64bae6dff027ea3efc1987@72.251.230.233:45120,fbf04b3d67705ed48831aa80ebe733775e672d1a@107.6.94.246:45110,5a6f0e342ea66cb769194c81141ffbff7417fbcd@72.251.230.233:45110"
```
- Save the file with CTRL+X write Y press Enter

## 6.Download Genesis File

```bash
curl https://newyork-inap-72-251-230-233.ankr.com/tac_tacd_testnet_full_tendermint_rpc_1/genesis | jq '.result.genesis' > .testnet/config/genesis.json
```

- Create a new screen session
```bash
screen -S Tac
```
## 7. Start Your Node
```bash
tacchaind start --chain-id tacchain_2390-1 --home .testnet
```
- Detach Screen: CTRL A+D


### DONE



















