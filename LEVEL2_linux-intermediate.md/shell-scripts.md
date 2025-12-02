````md
# 📌 Create Shell Scripts: Log Cleanup, Service Restart, Health Checks

This section includes simple shell scripts for common DevOps automation tasks.  
All scripts can be executed in Git Bash (SSH into Linux).

````

## 🧹 1. Log Cleanup Script

This script clears log files older than 7 days and frees disk space.

### 📄 cleanup-logs.sh
```bash
#!/bin/bash

# Directory to clean logs
LOG_DIR="/var/log"

# Delete logs older than 7 days
find $LOG_DIR -type f -mtime +7 -exec rm -f {} \;

echo "Old logs cleaned successfully!"
````

Make executable:

```bash
chmod +x cleanup-logs.sh
```

Run:

```bash
./cleanup-logs.sh
```

## 🔄 2. Service Restart Script

This script checks if a service is running; if not, it automatically restarts it.

### 📄 service-restart.sh

```bash
#!/bin/bash

SERVICE="nginx"

# Check if service is active
if systemctl is-active --quiet $SERVICE; then
    echo "$SERVICE is running."
else
    echo "$SERVICE is not running. Restarting..."
    sudo systemctl restart $SERVICE
fi
```

Make executable:

```bash
chmod +x service-restart.sh
```

Run:

```bash
./service-restart.sh
```

## ❤️ 3. Health Check Script

This script checks CPU, memory, disk usage, and top processes.

### 📄 health-check.sh

```bash
#!/bin/bash

echo "===== SYSTEM HEALTH CHECK ====="

echo
echo "📌 CPU Load:"
uptime

echo
echo "📌 Memory Usage:"
free -h

echo
echo "📌 Disk Usage:"
df -h

echo
echo "📌 Top 5 CPU Consuming Processes:"
ps aux --sort=-%cpu | head -5

echo
echo "📌 Top 5 RAM Consuming Processes:"
ps aux --sort=-%mem | head -5

echo
echo "Health check completed!"
```

Make executable:

```bash
chmod +x health-check.sh
```

Run:

```bash
./health-check.sh
```
