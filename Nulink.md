# Nulink

- VPS

- Ubuntu 20.04
  
  Minimum System Requirements

- 30GB available storage / 4GB RAM


You can rent a vps on **[Contabo](https://contabo.com/en/vps-c/)** or **[hetzner](https://www.hetzner.com/)*


Let's look at server rental using **[Contabo](https://contabo.com/en/vps-c/)** as an example



You can rent the cheapest server to install a node 



[![1.png](https://i.postimg.cc/L5cHBhXP/1.png)](https://postimg.cc/BPC9JS2Z)



The next step is to connect to the server for this I use MobaXterm


[![2.png](https://i.postimg.cc/hGXdKywP/2.png)](https://postimg.cc/Z9hRcc41)


# Server preparation

download the necessary packages

```
sudo apt update && sudo apt upgrade -y
```

# Open the port


```
apt install ufw -y
```


```
ufw allow ssh
ufw allow https
ufw allow http
ufw allow 9151
ufw enable
```

#  Download Geth 

```
wget https://gethstore.blob.core.windows.net/builds/geth-linux-amd64-1.10.23-d901d853.tar.gz
```

#  Unzip the downloaded installation package

```
tar -xvzf geth-linux-amd64-1.10.23-d901d853.tar.gz
```

#  log into your directory

```
cd geth-linux-amd64-1.10.23-d901d853/
```

#  Create an Ethereum account and key vault. 
Make up a password and save it, we will need it later

```
./geth account new --keystore ./keystore
```

#  Docker installation


# Add Docker's official GPG key:

```
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```

# Add the repository to Apt sources:

```
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

# Install the Docker packages

```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

```
sudo apt-get update
```

# Pull the latest NuLink image

```
docker pull nulink/nulink:latest
```

# Create a directory

```
cd /root
mkdir nulink
```

# Сhange the path to the secret key file
replace **$$$$$$** with your key that you generated earlier

cp /root/geth-linux-amd64-1.10.23-d901d853/keystore/$$$$$$$$$$$ /root/nulink

# give this directory permissions 777

```
chmod -R 777 /root/nulink
```

Let's set variables with our password . Enter the password you made up earlier

export NULINK_KEYSTORE_PASSWORD=<YOUR NULINK STORAGE PASSWORD>

export NULINK_KEYSTORE_PASSWORD=<YOUR NULINK STORAGE PASSWORD>
