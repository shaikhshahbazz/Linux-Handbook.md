````md
# 📌 Manage Logs Under /var/log

This section explains how to explore, read, and manage system and application logs stored inside `/var/log`.  
These commands work in Git Bash when connected to a Linux server via SSH.
````

## 📁 1. View Log Files

### 🔹 List all log files
```bash
ls -l /var/log
````

### 🔹 View logs of a specific service (example: nginx)

```bash
ls -l /var/log/nginx
```

## 📜 2. Read Log Files

### ✔ Show entire log

```bash
cat /var/log/syslog
```

### ✔ View log page-by-page

```bash
less /var/log/syslog
```

### ✔ View last 50 lines

```bash
tail -n 50 /var/log/syslog
```

### ✔ Live log monitoring (real-time)

```bash
tail -f /var/log/syslog
```

## 🔍 3. Search Inside Logs

### ✔ Search for a keyword (example: “error”)

```bash
grep -i "error" /var/log/syslog
```

### ✔ Search recursively in all logs

```bash
grep -iR "failed" /var/log
```

## 🧹 4. Clean Up Large Logs

### ✔ Clear a log file (without deleting the file)

```bash
sudo truncate -s 0 /var/log/syslog
```

### ✔ Delete old logs (example: files older than 7 days)

```bash
sudo find /var/log -type f -mtime +7 -delete
```

## 🔧 5. Check Disk Usage of Log Directory

```bash
du -sh /var/log
```

Example:

```
150M    /var/log
```

## 🔄 6. Restart Services After Log Rotation or Cleanup

```bash
sudo systemctl restart rsyslog
```

Check service status:

```bash
systemctl status rsyslog
```
