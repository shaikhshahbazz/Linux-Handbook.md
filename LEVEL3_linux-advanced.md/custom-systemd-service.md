````md
# 📌 Create Custom systemd Service for Your Application

Systemd allows you to create and manage custom services for your applications.  
This helps you automatically start apps on boot, restart them on failure, and manage logs centrally.
````

## 🗂️ 1. Create Your Application Script

Example: simple app script at `/opt/myapp/app.sh`

```bash
#!/bin/bash
echo "Application started..."
# your application commands here
````

Make it executable:

```bash
chmod +x /opt/myapp/app.sh
```

## ⚙️ 2. Create a Systemd Service File

Create a new service file:

```bash
sudo nano /etc/systemd/system/myapp.service
```

Add the following:

```
[Unit]
Description=My Custom Application Service
After=network.target

[Service]
Type=simple
ExecStart=/opt/myapp/app.sh
Restart=always
RestartSec=5
User=root

[Install]
WantedBy=multi-user.target
```

## 🔄 3. Reload Systemd Daemon

```bash
sudo systemctl daemon-reload
```

## ▶️ 4. Start the Service

```bash
sudo systemctl start myapp
```

Check status:

```bash
systemctl status myapp
```

## 🚀 5. Enable Service on Boot

```bash
sudo systemctl enable myapp
```

## 🛑 6. Stop or Restart the Service

Stop service:

```bash
sudo systemctl stop myapp
```

Restart service:

```bash
sudo systemctl restart myapp
```

## 📜 7. View Service Logs

Systemd logs are stored in the journal.

```bash
sudo journalctl -u myapp
```

Follow logs live:

```bash
sudo journalctl -u myapp -f
```
