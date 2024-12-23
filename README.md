# Abstract-node

![image](logo.png)

## Pre requisite

1. You need docker installed and docker compose (if you already have it installed move to the Usage section)

Follow the instruction from the official documentation : https://docs.docker.com/engine/install/ubuntu/

Or use the command below

```
sudo apt update -y && sudo apt upgrade -y
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update -y && sudo apt upgrade -y

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Test Docker
sudo docker run hello-world

```


###Clone the official repo

```
git clone https://github.com/Abstract-Foundation/abstract-node
cd abstract-node/external-node
```


Rename the testnet file to a docker compose
```
 cp testnet-external-node.yml docker-compose.yml
```

Start the container
```
docker compose up -d
```

Check the logs 

```
 docker logs -f testnet-node-external-node-1

```

Check and save your private keys
```
 cat ~/abstract-node/external-node/configs/testnet_consensus_secrets.yaml

```


Please try it if you find any issues please reach out to me on twitter : https://x.com/0xAJPanda
