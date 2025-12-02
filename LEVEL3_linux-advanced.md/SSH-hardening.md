````md
# 📌 SSH Hardening for Security

Securing SSH is an essential step in protecting Linux servers from unauthorized access.  
This section explains how to harden SSH using best practices such as disabling root login, using key-based authentication, updating configurations, and limiting access.

````
## 🔐 1. Update System Packages

```bash
sudo apt update -y
sudo apt upgrade -y
````

## 🔑 2. Enable Key-Based Authentication

### ✔ Generate SSH key on your local machine

```bash
ssh-keygen -t rsa -b 4096
```

### ✔ Copy key to server

```bash
ssh-copy-id user@server-ip
```

### ✔ Verify login works without password

```bash
ssh user@server-ip
```

---

## 🚫 3. Disable Password Authentication

Edit SSH configuration file:

```bash
sudo nano /etc/ssh/sshd_config
```

Find and modify:

```
PasswordAuthentication no
ChallengeResponseAuthentication no
UsePAM yes
```

Restart SSH:

```bash
sudo systemctl restart sshd
```

## 🚫 4. Disable Root Login

In `/etc/ssh/sshd_config`:

```
PermitRootLogin no
```

Restart SSH:

```bash
sudo systemctl restart sshd
```

## 🔢 5. Change Default SSH Port (Optional but Recommended)

Example: Change from `22` to `2222`

In `/etc/ssh/sshd_config`:

```
Port 2222
```

Restart SSH:

```bash
sudo systemctl restart sshd
```

## 🛑 6. Allow Only Specific Users to SSH

In `/etc/ssh/sshd_config`:

```
AllowUsers devops admin
```

Restart:

```bash
sudo systemctl restart sshd
```

## 🔒 7. Enable Firewall Rules for SSH

### ✔ Allow custom SSH port (example: 2222)

```bash
sudo ufw allow 2222/tcp
```

### ✔ Enable firewall

```bash
sudo ufw enable
```

### ✔ Check status

```bash
sudo ufw status
```

## ⚙️ 8. Limit SSH Connection Attempts (Fail2Ban)

Install fail2ban:

```bash
sudo apt install fail2ban -y
```

Example jail config:

```bash
sudo vi /etc/fail2ban/jail.local
```

Add:

```
[sshd]
enabled = true
port = 22
maxretry = 3
findtime = 10m
bantime = 1h
```

Restart fail2ban:

```bash
sudo systemctl restart fail2ban
```

## 🧪 9. Test SSH Security

### ✔ Check SSH status

```bash
systemctl status sshd
```

### ✔ Test login with key

```bash
ssh user@server-ip
```

### ✔ Verify fail2ban logs

```bash
sudo tail -f /var/log/fail2ban.log
```
