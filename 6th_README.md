## Assignment 6 - Linux Process Manager Scripts

This Folder contains Process Manager utilities that help monitor, list, and manage Linux processes using simple command-line options.

It includes:

- otProcessManager.sh – an extended process management utility

- ProcessManager.sh – a simpler version with core features

Both scripts rely on Linux commands like ps, grep, and awk to extract and process running system information.

---
### 1. otProcessManager.sh — Advanced Process Manager

The advanced version of process management tool.

#### 🔹 Features

List all running processes

  - Display PID, state, priority, and command

Filter processes by:

  - CPU usage

  - Memory usage

Search processes by alias or name

Add alias mappings for frequently used processes

Store process info in a lightweight local DB file ($HOME/.process_manager_db)

#### 🔹 Supported Commands
```bash
./otProcessManager.sh topProcess <count> cpu
./otProcessManager.sh topProcess <count> memory
./otProcessManager.sh list
./otProcessManager.sh addAlias <alias> <process_name>
./otProcessManager.sh removeAlias <alias>
./otProcessManager.sh showDetails <alias>
```

#### 🔹 Typical Output Example
```bash
Alias           PID     State   Priority   Script
mukesh          2382159 SN      19         /home/mukesh/sleep_svc.sh
```

#### 🔹 Concepts Used

  - ps for process extraction

  - Sorting via sort -k

  - Functions for modular operations

  - Local DB file for storing aliases

  - Case statements for command routing

Signal handling when needed

---

### ⚙️ 2. ProcessManager.sh — Basic Version

A simpler variant that covers the essential functionality.

#### 🔹 Features

- List top CPU-consuming processes

- List top memory-consuming processes

- Show process status

- Show process priority

- Lightweight and fast

#### 🔹 Supported Commands
```bash
./ProcessManager.sh topProcess 5 cpu
./ProcessManager.sh topProcess 5 memory
./ProcessManager.sh listProcessDetails
./ProcessManager.sh help
```

#### 🔹 Concepts Used

- Command-line argument parsing

- Use of ps -eo to fetch system stats

- Sorting using sort

- Conditional checks

- Case statements for operation selection

### 📦 Suggested Folder Structure
```bash
Assignment6
├── otProcessManager.sh
├── ProcessManager.sh
└── README.md
```
