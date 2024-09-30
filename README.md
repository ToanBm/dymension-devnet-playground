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
```Bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
docker version
```
```Bash
sudo usermod -aG docker ${USER}
```
### Install Go
```Bash
sudo rm -rf /usr/local/go
curl -L https://go.dev/dl/go1.22.4.linux-amd64.tar.gz | sudo tar -xzf - -C /usr/local
echo 'export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin' >> $HOME/.bash_profile
echo 'export PATH=$PATH:$(go env GOPATH)/bin' >> $HOME/.bash_profile
source .bash_profile
go version
```
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
- Choose `playground`
- Enter your `Rollapp ID`
- Save your `hub_sequencer` and `my_celes_key`
- Fund `hub_sequencer`: 20DYM , `my_celes_key`: 1TIA
- 
### Setup RollApp Endpoints
```Bash
curl https://get.telebit.io/ | bash
```
- Enter your Email & verify
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
- Choose `Sequencer`
- dymint rpc endpoint that you will provide (example: rpc.rollapp.dym.xyz): https://rpc.<your-account>.telebit.io
- rest endpoint that you will provide (example: api.rollapp.dym.xyz): https://rest.<your-account>.telebit.io
- evm rpc endpoint that you will provide (example: json-rpc.rollapp.dym.xyz): https://evm.<your-account>.telebit.io
### Start RollApp
```Bash
roller rollapp services load
```
```Bash
roller rollapp services start
```
```Bash
roller rollapp status
```
## 3. Relayer
### Setup IBC Connection
```Bash
roller relayer setup
```
- Save your `relayer-rollapp-key` & `relayer-hub-key`
- Fund `relayer-hub-key` with at least 20 dym tokens
### Run Relayer
```Bash
roller relayer services load
```
```Bash
roller relayer services start
```
## 4. eIBC client
### Setup eIBC Client
- Initialize eIBC client
```Bash
roller eibc init
```
- Configure eIBC client
```Bash
roller eibc fulfill rollapps set <rollapp_id> <fee-in-percentage>
```
```Bash
roller eibc fulfill denoms set <denom-on-the-token-registry> <fee-in-percentage>
```
- `<fee-in-percentage>` = 0.01
- `<denom-on-the-token-registry>` = YOUR-TOKEN
### Start eIBC client
```Bash
roller eibc services load
```
```Bash
roller eibc services start
```
```Bash
roller eibc funds
```

























































