````md
# 📌 Install Required Packages (git, nginx, java)

This section explains how to install the most commonly required DevOps tools on a Linux system using package managers.

## 🛠️ 1. Update System Packages

Before installing anything, always update your package index.

```bash
sudo apt update -y
sudo apt upgrade -y
````

## 🧰 2. Install Git

Git is required for version control and source code management.

```bash
sudo apt install git -y
```

Verify installation:

```bash
git --version
```

## 🌐 3. Install Nginx (Web Server)

Install Nginx:

```bash
sudo apt install nginx -y
```

Start and enable the service:

```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```

Check service status:

```bash
systemctl status nginx
```

## ☕ 4. Install Java (OpenJDK 11)

```bash
sudo apt install openjdk-11-jdk -y
```

Check Java version:

```bash
java -version
```
