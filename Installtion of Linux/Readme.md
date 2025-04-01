# MongoDB Installation on WSL  

## Prerequisites  
- Windows 10/11 with WSL2 enabled  
- Ubuntu installed via WSL  

## Step 1: Update Package List  
Open WSL terminal and run:  
```sh
sudo apt update && sudo apt upgrade -y
```

## Step 2: Import MongoDB Public Key  
```sh
curl -fsSL https://pgp.mongodb.com/server-7.0.asc | sudo gpg --dearmor -o /usr/share/keyrings/mongodb-server-keyring.gpg
```

## Step 3: Add MongoDB Repository  
```sh
echo "deb [signed-by=/usr/share/keyrings/mongodb-server-keyring.gpg] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-7.0.list
```

> ⚠️ Adjust `jammy` (Ubuntu 22.04) based on your WSL version. Use `focal` for Ubuntu 20.04.

## Step 4: Install MongoDB  
```sh
sudo apt update
sudo apt install -y mongodb-org
```

## Step 5: Start MongoDB  
Since WSL does not support `systemd` by default, start MongoDB manually:  
```sh
sudo mongod --dbpath /data/db --bind_ip 0.0.0.0
```

Alternatively, start it as a background process:  
```sh
sudo mkdir -p /data/db
sudo mongod --dbpath /data/db --logpath /var/log/mongodb.log --fork
```

## Step 6: Verify MongoDB is Running  
```sh
mongo
```
If connected successfully, you’ll see the MongoDB shell.

## Stopping MongoDB  
To stop MongoDB:  
```sh
sudo pkill mongod
```

## Enable MongoDB to Start Automatically  
Since `systemd` is not fully supported in WSL, use the following approach:  
```sh
echo 'sudo mongod --dbpath /data/db --bind_ip 0.0.0.0' >> ~/.bashrc
```
This will start MongoDB whenever you open a new WSL session.

---


