````md
# 📌 Automate Backups with Cron

This section covers how to automate backups using Cron on a Linux system.  
You can schedule backups of directories, logs, or configuration files.

---

## 🗂️ 1. Create a Simple Backup Script

Create a script that copies a folder to a backup location.

```bash
#!/bin/bash

# Source directory
SOURCE="/home/ubuntu/project"

# Backup directory
DEST="/home/ubuntu/backups"

# Create backup filename with date
FILENAME="backup-$(date +%F-%H-%M).tar.gz"

# Run backup
tar -czf $DEST/$FILENAME $SOURCE
````

Make script executable:

```bash
chmod +x backup.sh
```
## ⏱️ 2. Schedule Backup Using Cron

Open the crontab file:

```bash
crontab -e
```

### 📍 Example Cron Jobs

#### 🔹 Backup every day at 12 AM (midnight)

```bash
0 0 * * * /home/ubuntu/backup.sh
```

#### 🔹 Backup every 6 hours

```bash
0 */6 * * * /home/ubuntu/backup.sh
```

#### 🔹 Backup every Sunday at 2:30 AM

```bash
30 2 * * 0 /home/ubuntu/backup.sh
```
## 🧪 3. Verify Cron Jobs

List configured cron jobs:

```bash
crontab -l
```

Check Cron logs (Ubuntu):

```bash
sudo tail -f /var/log/syslog
```
