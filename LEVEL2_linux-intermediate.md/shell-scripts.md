````md
# 📌 Monitor System Performance and Troubleshoot Services
````
This section explains how to monitor system performance (CPU, RAM, disk, processes) and troubleshoot running services on a Linux server.  
These commands work in Git Bash when connected to a Linux machine via SSH.


## 📈 1. Monitor System Performance

### 🔹 Real-time system overview
```bash
top
````

### 🔹 Modern alternative with better UI

```bash
htop
```

(Install: `sudo apt install htop -y`)

## 🧠 2. Check Memory Usage

```bash
free -h
```

### 🔹 Find processes consuming most RAM

```bash
ps aux --sort=-%mem | head
```

## 🖥️ 3. Check CPU Usage

```bash
lscpu
```

### 🔹 Top CPU consumers

```bash
ps aux --sort=-%cpu | head
```

### 🔹 System load average

```bash
uptime
```

## 💽 4. Check Disk Usage

```bash
df -h
```

### 🔹 Check disk usage of a directory

```bash
du -sh /var/log
```

## 🔌 5. Check Running Services

### 🔹 Check service status (example: nginx)

```bash
systemctl status nginx
```

### 🔹 Start service

```bash
sudo systemctl start nginx
```

### 🔹 Stop service

```bash
sudo systemctl stop nginx
```

### 🔹 Restart service

```bash
sudo systemctl restart nginx
```

### 🔹 Enable service on system boot

```bash
sudo systemctl enable nginx
```

## 🔍 6. Check Service Logs

### 🔹 Using journalctl (systemd logs)

```bash
sudo journalctl -u nginx
```

### 🔹 See last 50 log entries

```bash
sudo journalctl -u nginx -n 50
```

### 🔹 Follow logs live

```bash
sudo journalctl -u nginx -f
```

## 🧪 7. Troubleshoot Service Failures

### 🔹 Check why service failed

```bash
sudo systemctl status <service-name>
```

### 🔹 View detailed error logs

```bash
sudo journalctl -xe
```

### 🔹 Check port usage

```bash
sudo ss -tulpn
```

Example: find which service is using port 80.

## 🧯 8. Restart System Log Service

```bash
sudo systemctl restart rsyslog
```
