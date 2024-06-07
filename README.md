``` 
sudo apt update && sudo apt upgrade -y
sudo apt install -y curl git jq lz4 build-essential screen

sudo apt update && sudo apt install apt-transport-https ca-certificates curl software-properties-common -y && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - && sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" && sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin && sudo apt-get install docker-compose-plugin 
 
 
sudo apt install git-all 
 
 
sudo apt-get remove docker docker-engine docker.io containerd runc 
 
 
sudo apt-get update 
 
sudo apt-get install ca-certificates curl gnupg lsb-release 
 
 
sudo mkdir -m 0755 -p /etc/apt/keyrings 
 
 
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg 
 
echo  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null 
 
 
sudo apt-get update 
 
 
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin 
 
sudo docker run hello-world 
```


```

git clone https://github.com/ritual-net/infernet-container-starter

cd infernet-container-starter

```


```
screen -S ritual

project=hello-world make deploy-container

````

Press control+A+D  


https://basescan.org/address/0x8d871ef2826ac9001fb2e33fdd6379b6aabf449c#writeContract  


````

nano ~/infernet-container-starter/deploy/config.json

````
"registry_address": "0x3B1554f346DFe5c482Bb4BA31b880c1C18412170",  
change rpc_url to https://base-rpc.publicnode.com  
change private_key to your wallet's private key.  

Press crtl+x  
press y  
press enter  


```
nano ~/infernet-container-starter/projects/hello-world/contracts/Makefile
```
change sender's address to your wallet's private key.  
change RPC_URL to https://base-rpc.publicnode.com  
Press crtl+x  
press y  
press enter  

```
nano ~/infernet-container-starter/projects/hello-world/contracts/script/Deploy.s.sol
```
"registry_address": "0x3B1554f346DFe5c482Bb4BA31b880c1C18412170",  
Press crtl+x  
press y  
press enter  

```
nano ~/infernet-container-starter/projects/hello-world/container/config.json
```

"registry_address": "0x3B1554f346DFe5c482Bb4BA31b880c1C18412170",  
change private_key to your wallet's private key.  

Press crtl+x  
press y  
press enter  

```
cd deploy 

nano docker-compose.yaml

```

check your image version must to be 1.0.0  

Press crtl+x  

```
docker compose down
docker compose up -d
```

```
docker restart infernet-node
docker restart hello-world
docker restart deploy-redis-1
docker restart infernet-anvil
docker restart deploy-fluentbit-1

```

```
cd
mkdir foundry
cd foundry
curl -L https://foundry.paradigm.xyz | bash
source ~/.bashrc
foundryup

```
```
cd
cd infernet-container-starter/projects/hello-world/contracts/lib/
rm -r forge-std
rm -r infernet-sdk
forge install --no-commit foundry-rs/forge-std
forge install --no-commit ritual-net/infernet-sdk
```

```
cd
cd infernet-container-starter
project=hello-world make deploy-contracts

```


pick deployed sayshello address
```
nano ~/infernet-container-starter/projects/hello-world/contracts/script/CallContract.s.sol
```
put it there  
Press crtl+x  
press y  
press enter  

```
make call-contract project=hello-world
```


docker ps -a

docker logs <CONTAINER ID>

