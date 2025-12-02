````md
# 📌 Implement logrotate for App Logs

Logrotate is a Linux utility used to automatically rotate, compress, and manage log files.  
Using logrotate prevents logs from filling up disk space and helps maintain long-term log history.

This section explains how to configure log rotation for custom application logs.
````

## 🗂️ 1. Create Application Log Directory

```bash
sudo mkdir -p /var/log/myapp
sudo touch /var/log/myapp/app.log
````

## 🛠️ 2. Create Logrotate Configuration File

Create a custom logrotate file for your application:

```bash
sudo nano /etc/logrotate.d/myapp
```

Add the following configuration:

```
/var/log/myapp/*.log {
    daily
    rotate 7
    compress
    missingok
    notifempty
    copytruncate
}
```

### 🔹 Explanation

* **daily** → rotate logs every day
* **rotate 7** → keep 7 days of logs
* **compress** → compress older logs as `.gz`
* **missingok** → do not show error if log file missing
* **notifempty** → do not rotate if file is empty
* **copytruncate** → truncate log file after copying (useful for apps that keep file open)

## 🔍 3. Test Logrotate Configuration

Run a test:

```bash
sudo logrotate -d /etc/logrotate.d/myapp
```

(Only simulates rotation without doing it)

## 🔄 4. Force Log Rotation (for testing)

```bash
sudo logrotate -f /etc/logrotate.d/myapp
```

After rotation, check:

```bash
ls -l /var/log/myapp
```

Example output:

```
app.log
app.log.1.gz
app.log.2.gz
```

## 🗓️ 5. Verify Logrotate Cron Job

Logrotate runs daily via cron:

```bash
cat /etc/cron.daily/logrotate
```

You can also check logs:

```bash
sudo tail -f /var/log/syslog
```
