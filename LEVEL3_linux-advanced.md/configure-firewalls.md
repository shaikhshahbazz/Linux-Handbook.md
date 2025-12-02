````md
# 📌 Configure Firewall Rules (UFW)

Configuring firewall rules helps secure your server by controlling which network traffic is allowed or blocked.  
This guide uses **UFW (Uncomplicated Firewall)** — the default firewall on Ubuntu.
````

## 🔥 1. Install UFW (if not installed)

```bash
sudo apt install ufw -y
````

Check status:

```bash
sudo ufw status
```

## 🔓 2. Allow Essential Ports

### ✔ Allow SSH (port 22 or custom port)

```bash
sudo ufw allow 22/tcp
```

If you changed SSH port (example: 2222):

```bash
sudo ufw allow 2222/tcp
```

### ✔ Allow HTTP (port 80)

```bash
sudo ufw allow 80/tcp
```

### ✔ Allow HTTPS (port 443)

```bash
sudo ufw allow 443/tcp
```

## 🔒 3. Deny Unwanted Ports

Example: Deny port 8080:

```bash
sudo ufw deny 8080/tcp
```

## 🚀 4. Enable UFW Firewall

```bash
sudo ufw enable
```

Confirm:

```bash
sudo ufw status verbose
```

## 🧱 5. Allow Specific IP Only (More Secure)

Example: Only allow SSH from your office IP:

```bash
sudo ufw allow from <IP_ADDRESS> to any port 22
```

Example:

```bash
sudo ufw allow from 203.0.113.50 to any port 22
```

## 🎯 6. Allow Specific Subnet

```bash
sudo ufw allow from 192.168.1.0/24 to any port 80
```

## 🚫 7. Block an IP Address

```bash
sudo ufw deny from 35.170.22.15
```

## ♻️ 8. Reset All UFW Rules

If something breaks:

```bash
sudo ufw reset
```

## 📋 9. View All Rules

```bash
sudo ufw status numbered
```

## 🗑️ 10. Delete a Rule

Example: Delete rule number 4:

```bash
sudo ufw delete 4
```
