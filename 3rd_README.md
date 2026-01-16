### 🔐 SSH Config Manager Script

This script automates the creation, updating, deletion, and listing of SSH configuration entries inside:
a new line
```
~/.ssh/config
```

It helps you quickly add SSH hosts, generate key pairs, update entries, and connect to servers using shortcuts.

---
## 📂 What This Script Uses (Technical Breakdown)

This script is built using core Bash features:

### 🧩 **1. `getopts` for Argument Parsing**
Used to accept parameters like:
- `-a` (add)
- `-n` (server name)
- `-h` (host / IP)
- `-u` (username)
- `-p` (port)
- `-i` (identity file)
- `-U` (update mode)

### 🧩 **2. Functions**
Script is modular, each task handled separately:
- `ssh_dir` → Creates `.ssh` directory and config  
- `add_server_name` → Adds `Host <name>`  
- `add_user` → Adds HostName & User  
- `add_port` → Adds Port  
- `copy_identity_file` → Generates & adds SSH key  
- `connect_to_server` → SSH connection logic  
- `update_ssh_connection` → Modify existing config  
- `list_SSH_entries` → Show saved hosts  
- `delete_ssh_entry` → Remove entry  

### 🧩 **3. Case Statements**
Used to handle:
- `ls` → list entries  
- `rm` → remove entry  
- Default fallbacks  

### 🧩 **4. Grep, Sed, Awk**
Used for reading & modifying SSH config blocks.

### 🧩 **5. Here-Documents (`cat <<EOF`)**
Used to append structured SSH blocks to the config file.

---

## ✨ Features

### ✔ Add a new SSH Host entry  
- Adds `Host`, `HostName`, `User`, and optional `Port` / `IdentityFile`  
- Automatically creates `~/.ssh` and config file if not present  
- Prevents duplicate hostnames or server names  

### ✔ Generate SSH Keys automatically  
- Creates a key pair for a specific user  
- Places the public key inside your current user's `.ssh` directory  
- Appends `IdentityFile` entry to the config  

### ✔ Update an existing SSH Host entry  
- Update HostName  
- Update User  
- Update Port  

### ✔ Direct SSH connection  
- If you pass a server name directly, script automatically reads from config and connects  

### ✔ List saved SSH entries  
- List only server names  
- Or list full SSH commands (`ssh -i key -p port user@host`)  

### ✔ Delete a host entry  
- Removes all lines under a Host block (Host, HostName, User, Port, IdentityFile)

---

## 🧰 Usage

### **Add a new SSH server**
```
./otssh.sh -a -n <server_name> -h <ip_addr> -u <username> [-p <port>] [-i <identity_file>]
```

Example:
```./otssh.sh -a -n server1 -h 192.168.1.10 -u kirti -p 2222```

---

## 🔑 Generate SSH Key During Add
When you include `-i`, a new key is generated for the target user:

```
./otssh.sh -a -n server2 -h 10.0.0.5 -u ubuntu -i  ~/.ssh/ubuntu.pem
```

This will:
- Generate `/home/ubuntu/.ssh/ubuntu.pem.pub`
- Copy `.pub` key to current user `.ssh/`
- Add `IdentityFile` entry in config

---

## 🛠 Update Existing Entry
```
./otssh.sh -U -n <server_name> -h <new_ip> -u <new_user> -p <new_port>
```

Example:
```./otssh.sh -U -n server2 -h 10.1.1.9 -u kirti -p 2200```

---

## 📜 List SSH Entries

### List only server names:
```
./otssh.sh ls
```

### List full details with SSH command:
```
./script.sh ls -d
```

Example Output:
```server3: ssh -i /home/ubuntu/.ssh/ubuntu.pem -p 2222 ubuntu@192.168.1.10```

---

## ❌ Delete SSH Entry
```
./otssh.sh rm <server_name>
```

Example:
```./otssh.sh rm server3```

---

## 🚀 Connect Directly (Shortcut Mode)
If server exists in config, simply run:

```
./otssh.sh <server_name>
```

Example:
```./otssh.sh server3```

The script automatically:
- Fetches HostName, User, Port, Key  
- Connects using SSH  

---

## 📂 Where Config Is Stored

```
~/.ssh/config
```

The script ensures:
- Directory exists  
- Config file exists  
- Correct permissions (700 for `.ssh`, 600 for config)

---

## 🛡 Safety Checks
The script validates:
- Missing required arguments  
- Duplicate server/hostnames  
- Missing config file  
- Port conflicts  
- Key file permissions  
- That a host exists before connecting or deleting  

---

## ✔ Example SSH Config Block Added by Script

```
Host server3
    HostName 192.168.1.10
    User ubuntu
    Port 2222
    IdentityFile /home/ubuntu/.ssh/ubuntu_id_rsa
```
