# dymension-devnet-playground

## 1. Setup Environment
### Install essentials
```Bash
sudo apt update && sudo apt upgrade -y
```
```Bash
sudo apt install -y build-essential clang curl aria2 wget tar jq libssl-dev pkg-config make
```
### Install Docker

### Install Go


### Install Roller
```Bash
curl https://raw.githubusercontent.com/dymensionxyz/roller/main/install.sh | bash
```
```Bash
roller version
```
## 2. Start Sequencer
### Initialize RollApp Directory
```Bash
roller rollapp init
```
Choose `playground` and enter your `Rollapp ID`

### Setup RollApp Endpoints
```Bash
curl https://get.telebit.io/ | bash
```
```Bash
~/telebit http 1317 rest
~/telebit http 8545 evm
~/telebit http 26657 rpc
```
```Bash
~/telebit save
```
### Setup RollApp Sequencer
```Bash
roller rollapp setup
```
Choose `Sequencer` 

Start RollApp
```Bash
roller rollapp services load
```
```Bash
roller rollapp services start
```
```Bash
roller rollapp status
```

























