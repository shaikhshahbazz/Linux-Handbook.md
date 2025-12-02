````md
# 📌 Check System Info (Memory, CPU, Disks)
````
This section explains how to check system information such as memory usage, CPU details, and disk storage on a Linux system. These commands work in Git Bash (when connected to a Linux server via SSH).

## 🧠 1. Check Memory Usage
````
### 🔹 Show memory summary
```bash
free -h
````
### 🔹 Detailed real-time memory usage

```bash
top
```

### 🔹 Modern alternative to top

```bash
htop
```

(Install if missing: `sudo apt install htop -y`)

## 🖥️ 2. Check CPU Information

### 🔹 CPU details (cores, model, speed)

```bash
lscpu
```

### 🔹 Top processes by CPU load

```bash
top
```

### 🔹 CPU load averages

```bash
uptime
```

Example output:

```
load average: 0.15, 0.10, 0.05
```

## 💽 3. Check Disk Storage

### 🔹 Disk usage summary (human-readable)

```bash
df -h
```

### 🔹 Directory-wise disk usage

```bash
du -sh /var/log
```

### 🔹 Detailed directory breakdown

```bash
du -sh * 
```
