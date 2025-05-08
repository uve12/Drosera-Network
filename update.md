# Update Drosera v1.17.1

### Update droseraup Utility

```
curl -L https://app.drosera.io/install | bash
source ~/.bashrc
droseraup
```

### Stop docker

```
cd ~/Drosera-Network
docker compose down -v
```

### Update `drosera.toml`  File

```
cd ~/my-drosera-trap
nano drosera.toml
```
Please update the `drosera_rpc` field to point to the new Drosera relay server at `https://relay.testnet.drosera.io`.

Example `See the difference1` : 

```
#old 
drosera_rpc = "https://seed-node.testnet.drosera.io"

#new
drosera_rpc = "https://relay.testnet.drosera.io"
```

Final should be like this

<img width="683" alt="DroseraNew" src="https://github.com/user-attachments/assets/1c860e0d-5e33-4134-9eea-a4d0c47bc262" />

### Re-apply Trap

```
DROSERA_PRIVATE_KEY=your_private_key drosera apply
```

use first wallet private_key

Type ofc in the cmd

### Restart Operators

```
cd ~/Drosera-Network
docker compose up -d
```

---

**Follow** : https://x.com/cryptoconsol
