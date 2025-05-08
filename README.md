# Drosera-Network
Setup Drosera Network Multiple Trap Operator in One VPS

Drosera is the security automation layer for operators and protocols. Crypto without Compromise.

Site : [Drosera](https://www.drosera.io/) | X : [DroseraX](https://x.com/DroseraNetwork) | Docs : [Drosera docs](https://dev.drosera.io/docs/intro/)

---

# Join Crypto Console Community

Join TG : [Crypto Console Telegram](https://t.me/cryptoconsol) 

Follow X : [Crypto Console Twitter](https://www.x.com/cryptoconsol) 

Subscribe : [Crypto Console Youtube](https://www.youtube.com/@cryptoconsole)


---

# VPS Options

💻 Contabo VPS Deals 🚀 Buy with Credit Card/Paypal/Crypto Credit card : 

Get powerful VPS solutions with these direct links:  

VPS 4C : [contabo VPS 4C](https://www.kqzyfj.com/click-101278318-13796470)

VPS 6C : [Contabo VPS 6C](https://www.kqzyfj.com/click-101278318-13796472)

VPS 8C : [Contabo VPS 8C](https://www.tkqlhce.com/click-101278318-13796474)

VPS 10C : [Contabo VPS 10C](https://www.anrdoezrs.net/click-101278318-13796476)

VPS 14C : [contabo VPS 14C](https://www.kqzyfj.com/click-101278318-15807107)

---

## Hardware requirements:

| **Hardware** | **Minimum Requirement** |
|--------------|-------------------------|
| **CPU**      | 2 Cores                 |
| **RAM**      | 4 GB                    | 
| **Disk**     | 30 GB  SSD              |

---

# 🚨 Drosera Network Testnet Guide

This guide helps you contribute to the **Drosera Testnet** by:

✅ Installing the CLI  
✅ Setting up a vulnerable contract  
✅ Deploying a trap  
✅ Connecting an operator

---

Create an **Ethereum Holesky RPC** from:  
🔹 [Alchemy](https://dashboard.alchemy.com/)  
🔹 [drpc](https://drpc.org/)

---

## ⚙️ Step 1: Install Dependencies

### Update & Upgrade
```bash
sudo apt update && sudo apt upgrade
```

### Install Required Packages
```bash
sudo apt install curl ufw iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip 
```


## 🐳 Step 2: Install Docker

```bash
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
```


## 🧪 Step 3: Trap Setup

### 3.1 Install CLIs

**Drosera CLI**
```bash
curl -L https://app.drosera.io/install | bash
source ~/.bashrc
droseraup
```

**Foundry CLI**
```bash
curl -L https://foundry.paradigm.xyz | bash
source ~/.bashrc
foundryup
```

**Bun**
```bash
curl -fsSL https://bun.sh/install | bash
source ~/.bashrc
```

### 3.2 Deploy Contract & Trap

```bash
mkdir my-drosera-trap && cd my-drosera-trap
```

Configure Git:
```bash
git config --global user.email "Your_GitHub_Email"
git config --global user.name "Your_GitHub_Username"
```

Initialize Trap:
```bash
forge init -t drosera-network/trap-foundry-template
```
```
curl -fsSL https://bun.sh/install | bash
source /root/.bashrc
bun install
```
```
forge build
```

**Holesky Faucet** : https://cloud.google.com/application/web3/faucet

Deploy the Trap:
```bash
DROSERA_PRIVATE_KEY=your_private_key drosera apply
```
> Replace `your_private_key` with your funded Holesky wallet key.
> Type ofc and press enter

### 🔍 Step 4: View Trap on Dashboard

1. Visit [Drosera Dashboard](https://app.drosera.io/)
2. Connect your EVM wallet.
3. Check **"Traps Owned"** or search your Trap address.

### 🌸 Step 5: Boost the Trap

Go to your Trap on the dashboard → Click **Send Bloom Boost** → Deposit Holesky ETH.

### 📦 Step 6: Fetch Blocks

```bash
drosera dryrun
```

---

# 👷 Operator Setup

### 🔐 Step 1: Whitelist Operator

Edit the Trap config:
```bash
cd ~/my-drosera-trap
nano drosera.toml
```

Paste the below at bottom:
```toml
private_trap = true
whitelist = ["Your_Operator_Address"]
```
**Replace Operator_Address with your EVM wallet address**

CTRL + X, Y and Enter

```bash
DROSERA_PRIVATE_KEY=your_private_key drosera apply
```

---

### 🛠️ Step 2: Install Operator CLI

```bash
cd ~
curl -LO https://github.com/drosera-network/releases/releases/download/v1.16.2/drosera-operator-v1.16.2-x86_64-unknown-linux-gnu.tar.gz
tar -xvf drosera-operator-*.tar.gz
sudo cp drosera-operator /usr/bin
```

Test it:
```bash
./drosera-operator --version
drosera-operator
```

### 🐋 Step 3: Pull Docker Image

```bash
docker pull ghcr.io/drosera-network/drosera-operator:latest
```

### 📝 Step 4: Register Operator

```bash
drosera-operator register --eth-rpc-url https://ethereum-holesky-rpc.publicnode.com --eth-private-key your_private_key
```

### 🔓 Step 5: Open Firewall Ports

```bash
sudo ufw allow ssh
sudo ufw allow 22
sudo ufw allow 31313/tcp
sudo ufw allow 31314/tcp
sudo ufw enable
```

### ⚙️ Step 6: Run the Operator

Clone repo & configure:
```bash
git clone https://github.com/uve12/Drosera-Network
cd Drosera-Network
cp .env.example .env
nano .env
```

Edit `.env` with your private key and VPS IP.  
Then edit `docker-compose.yaml` and replace the RPC URL.
```
nano docker-compose.yaml
```
Start the Operator:
```bash
docker compose up -d
```

Check logs:
```bash
docker logs -f drosera-node1
```

✅ Warning logs like `InsufficientPeers` can be ignored.

---

## 🔗 Step 7: Connect Operator to Trap

On the dashboard → click **Opt-in** → confirm.

---

## ✅ Step 8: Verify Node Liveness

Once active, check dashboard your node will produce **green blocks**.

---

# ➕ Add a 2nd Operator

1. Create a new EVM wallet  
2. Fund with Holesky ETH  

Edit configurations:

```
cd ~/my-drosera-trap
nano drosera.toml
```

3. Save its public/private keys


Update whitelist in `drosera.toml`:
```toml
whitelist = ["1st_Operator_Address", "2nd_Operator_Address"]
```

Then:
```bash
DROSERA_PRIVATE_KEY=your_private_key drosera apply
```
**use first wallet private_key**

Register the 2nd Operator:
```bash
drosera-operator register --eth-rpc-url https://ethereum-holesky-rpc.publicnode.com --eth-private-key 2nd_operator_privatekey
```

Open additional ports:
```bash
sudo ufw allow 31315/tcp
sudo ufw allow 31316/tcp
```

Edit yaml 
```
cd $HOME/Drosera-Network
```
```
docker compose down -v
docker stop drosera-node1
docker rm drosera-node1
```
```
nano docker-compose.yaml
```

```
version: '3'
services:
  drosera1:
    image: ghcr.io/drosera-network/drosera-operator:latest
    container_name: drosera-node1
    network_mode: host
    volumes:
      - drosera_data1:/data
    command: node --db-file-path /data/drosera.db --network-p2p-port 31313 --server-port 31314 --eth-rpc-url RPC_URL_1 --eth-backup-rpc-url https://holesky.drpc.org --drosera-address 0xea08f7d533C2b9A62F40D5326214f39a8E3A32F8 --eth-private-key ${ETH_PRIVATE_KEY} --listen-address 0.0.0.0 --network-external-p2p-address ${VPS_IP} --disable-dnr-confirmation true
    restart: always

  drosera2:
    image: ghcr.io/drosera-network/drosera-operator:latest
    container_name: drosera-node2
    network_mode: host
    volumes:
      - drosera_data2:/data
    command: node --db-file-path /data/drosera.db --network-p2p-port 31315 --server-port 31316 --eth-rpc-url RPC_URL_2 --eth-backup-rpc-url https://holesky.drpc.org --drosera-address 0xea08f7d533C2b9A62F40D5326214f39a8E3A32F8 --eth-private-key ${ETH_PRIVATE_KEY2} --listen-address 0.0.0.0 --network-external-p2p-address ${VPS_IP} --disable-dnr-confirmation true
    restart: always

volumes:
  drosera_data1:
  drosera_data2:
```

**Replace RPC URL**

Update `docker-compose.yaml` to add second operator service.

Edit .env:
```
nano .env
```

**Replace all details with credentials**

```
ETH_PRIVATE_KEY=
ETH_PRIVATE_KEY2=
VPS_IP=
P2P_PORT1=31313
SERVER_PORT1=31314
P2P_PORT2=31315
SERVER_PORT2=31316
```
### Run Multiple operator

Start Operator
```
docker compose up -d
```

opt-in operator

```
drosera-operator optin --eth-rpc-url https://ethereum-holesky-rpc.publicnode.com --eth-private-key 2nd_Operator_Privatekey --trap-config-address Trap_Address
```
**Replace 2nd_Operator_Privatekey & Trap_Address**

Restart Operators

```
cd ~/Drosera-Network
docker compose down -v
docker compose up -d
```

---

**Follow** : https://x.com/cryptoconsol



