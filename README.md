# Abstract-node

![image](logo.png)

## Pre-requisites

Before getting started, make sure you have Docker and Docker Compose installed on your system. If you don’t have them installed, follow the steps below:

### Install Docker and Docker Compose

Follow the official [Docker installation guide for Ubuntu](https://docs.docker.com/engine/install/ubuntu/) or run the following commands:

```bash
# Update your system
sudo apt update -y && sudo apt upgrade -y

# Remove conflicting packages
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

# Install dependencies
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg

# Install Docker
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Add Docker's official repository
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Update and install Docker and Docker Compose
sudo apt update -y && sudo apt upgrade -y
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Test Docker installation
sudo docker run hello-world
```

## Clone the Official Repository

First, clone the repository to your local machine:

```bash
git clone https://github.com/Abstract-Foundation/abstract-node
cd abstract-node/external-node
```

### Rename the Testnet File to Docker Compose

Rename the testnet file to `docker-compose.yml`:

```bash
cp mainnet-external-node.yml docker-compose.yml
```

### Start the Container

Launch the container using Docker Compose:

```bash
docker compose up -d
```

### Check the Logs

To monitor the logs of the container:

```bash
docker logs -f testnet-node-external-node-1
```

### Check and Save Your Private Keys

The private key is inside the node itself, i will provide the command to retrive it in the next commit

## Troubleshooting

### Issue: PostgreSQL Not Starting

Many users have reported issues with PostgreSQL not starting. The easiest solution to resolve this is to bring the container down and start it again:

```bash
docker compose down && docker compose up -d
```

If you encounter any other issues, feel free to reach out to me on Twitter: [@0xAJPanda](https://x.com/0xAJPanda).

