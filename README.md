# 👥 User & Team Management Script
A simple Bash automation script to manage **Linux users, teams (groups), home directories, and permissions**.

This script provides an easy interface for system administrators to manage teams, users, shells, passwords, and shared directories — all using a single command-line tool.

---

## 📦 Features

### ✔ Team Management
- Create a new team (Linux group)
- Allocate team directory under `/home/<team>`
- Assign permissions (`770`) for secure access
- Delete existing teams (only if no users are assigned)

### ✔ User Management
- Create users with home directories `/home/<user>`
- Assign user to a specific team
- Automatically join the **shared “ninja” group**
- Auto-create shared directories:
  - `/home/<user>/team` (team access)
  - `/home/<user>/ninja` (shared access)
- Delete users (with home directory)

### ✔ Shell & Password Updates
- Change user shell
- Change user password

### ✔ Listing
- List all users under `/home`
- List all Teams (groups)

---

## 📁 Directory Structure Created
```
/home/
└── <username>/ # User home directory (751)
  ├── team/ # Team shared folder (770)
  └── ninja/ # Ninja shared folder (770)
```
---

## 🔧 Requirements
- Script must be executed with **sudo/admin privileges**.
- Linux system with standard utilities: `groupadd`, `useradd`, `usermod`, `chmod`, `chgrp`, `passwd`.

---

## 🚀 Usage

### **Add a Team**
```
./UserManager.sh addTeam <team>
```
Example:
```./UserManager.sh addTeam devops ```

---

### **Add a User**
```
./userManager.sh addUser <user> <team>
```
Example:
```./UserManager.sh addUser mukesh devops```

This automatically:
- Creates `/home/mukesh`
- Adds the user to team `devops`
- Adds the user to group `ninja`
- Creates shared folders `/team` and `/ninja`

---

### **Delete a User**
```
./UserManager.sh delUser <user>
```
Example:
```./UserManager.sh delUser mukesh```

---

### **Delete a Team**
```
./userMamager.sh delTeam <team>
```

⚠ Teams can only be deleted when **no users belong to them**.

Example:
```./UserManager.sh delTeam devops```

---

### **Change User Shell**
```
./UserManager.sh changeShell <user> <shell>
```

Example:
```./UserManager.sh changeShell mukesh /bin/zsh```

---

### **Change User Password**
```
./UserManager.sh changePasswd <user>
```

---

### **List Users or Teams**
```
./UserManager.sh ls User
./UserManager.sh ls Team
```

---

## 🔐 Permission Behavior

| Path | Owner | Group | Mode | Purpose |
|------|-------|--------|------|---------|
| `/home/<user>` | `<user>` | `<team>` | 751 | Private home |
| `/home/<user>/team` | `<user>` | `<team>` | 770 | Team-only content |
| `/home/<user>/ninja` | `<user>` | ninja | 770 | Cross-team shared |

---

## 🧩 Error Handling
The script validates:

- Missing arguments  
- User existence  
- Group existence  
- Group deletion only if no users assigned  
- Shell path & user existence  
- Ensures `ninja` group exists only once  

---

## 📘 Notes
- The script starts with:
#!/usr/bin/sudo /bin/bash

This ensures it **runs with sudo**.
- Modify the `BASE` variable if you want home directories in another path.

---
## Author
Mukesh Kharb
