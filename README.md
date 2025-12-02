# linux-handbook
├── README.md
│   ├── LEVEL1_BASIC.md
│   ├── LEVEL2_INTERMEDIATE.md
│   ├── LEVEL3_ADVANCED.md
└── docs/
    └── OVERVIEW.md

# Linux Server Setup & Automation Roadmap
A complete learning roadmap for becoming production-ready in Linux administration, designed for DevOps and platform engineers.

## 📌 Levels Overview
This roadmap is divided into four progressive levels:

- *Level 1 — Basic:* Foundation of Linux server administration  
- *Level 2 — Intermediate:* Daily DevOps operations  
- *Level 3 — Advanced:* Production-ready systems    

Each level is detailed in the /roadmap folder.

---

## 📂 Roadmap Files

- [Level 1 — Basic](LEVEL1_BASIC.md)
- [Level 2 — Intermediate](LEVEL2_INTERMEDIATE.md)
- [Level 3 — Advanced](LEVEL3_ADVANCED.md)

---

## 📚 Documentation
Additional overview and explanation in:  
➡ /docs/OVERVIEW.md

---

## 🔧 Ideal For
- DevOps engineers  
- Sysadmins  
- SRE beginners  
- Anyone building production Linux systems  

---
Below is an *expanded “Additional Linux Knowledge” section* that you can append to your README.md, or use separately to strengthen your Linux fundamentals and DevOps readiness.

I organized it into the *most practical areas* every DevOps engineer uses daily: commands, processes, networking, storage, security, system internals, and troubleshooting.

---

# 📘 Additional Linux Knowledge (Extended DevOps Edition)

---

## 🧠 1. Linux Directory Structure (FHS – Filesystem Hierarchy Standard)

| Directory                                | Purpose                                   |
| ---------------------------------------- | ----------------------------------------- |
| /                                      | Root directory                            |
| /home                                  | User home directories                     |
| /root                                  | Root user’s home                          |
| /etc                                   | System configuration files                |
| /var                                   | Logs, cache, spool files                  |
| /var/log                               | System and application logs               |
| /usr                                   | User applications, binaries, libraries    |
| /bin, /sbin, /usr/bin, /usr/sbin | Executable commands                       |
| /opt                                   | Optional third-party software             |
| /tmp                                   | Temporary files                           |
| /mnt, /media                         | Mounted drives                            |
| /dev                                   | Device files (disks, partitions, USB)     |
| /proc                                  | Virtual system info (CPU, memory, kernel) |
| /sys                                   | Kernel and device info                    |

---

## ⚙ 2. Essential Commands (Cheat Sheet)

### File Navigation

bash
ls -l
cd /path
pwd


### File Content

bash
cat file
less file
head -n 20 file
tail -f logfile


### File Management

bash
cp src dst
mv old new
rm file
mkdir folder
touch file


### Permissions

bash
chmod 755 file
chown user:group file


---

## 🧵 3. Process Management

### View Processes

bash
ps aux
top
htop


### Find a Process

bash
ps aux | grep nginx


### Kill a Process

bash
kill PID
kill -9 PID


### Check Service Status (systemd)

bash
systemctl status nginx
systemctl start nginx
systemctl stop nginx
systemctl restart nginx


---

## 🌐 4. Linux Networking Essentials

### Check IP Address

bash
ip a


### Test Connectivity

bash
ping google.com
curl -I http://example.com


### Check Open Ports

bash
ss -tulpn
netstat -tulnp


### DNS Lookup

bash
nslookup example.com
dig example.com


### Firewall (UFW)

bash
sudo ufw status
sudo ufw allow 80/tcp
sudo ufw enable


---

## 📡 5. Package Management

### Ubuntu/Debian

bash
apt update
apt install pkg
apt remove pkg
dpkg -i package.deb


### RHEL/CentOS

bash
dnf install pkg
yum install pkg
rpm -ivh file.rpm


---

## 💽 6. Storage & Filesystems

### List Drives

bash
lsblk
fdisk -l


### Mount Storage

bash
mount /dev/sdb1 /mnt/data
umount /mnt/data


### Filesystem Operations

bash
mkfs.ext4 /dev/sdb1
fsck /dev/sdb1
df -h          # check disk usage
du -sh folder  # folder size


---

## 📦 7. Archives & Compression

### Create Tar/Gzip

bash
tar -czf file.tar.gz folder/


### Extract

bash
tar -xzf file.tar.gz


### Zip / Unzip

bash
zip -r file.zip folder/
unzip file.zip


---

## 🛡 8. Linux Security Basics

### File Permissions

bash
chmod 640 file
chown appuser:app file


### Sudoers

bash
visudo


Example permission:


devuser ALL=(ALL) NOPASSWD: /usr/bin/systemctl restart nginx


### Fail2ban

bash
sudo apt install fail2ban -y


---

## 🧰 9. System Information & Diagnostics

### Kernel Version

bash
uname -r


### OS Release

bash
cat /etc/os-release


### Uptime / Load Average

bash
uptime


### Hardware Info

bash
lshw
lscpu
lsusb
lspci


### Memory

bash
free -h


---

## 🟦 10. Logs & Troubleshooting

### System Logs

bash
journalctl -xe
journalctl -u nginx


### Log Files in /var/log

Common:

* /var/log/syslog
* /var/log/auth.log
* /var/log/nginx/access.log
* /var/log/nginx/error.log

### Search Logs

bash
grep -i "error" /var/log/syslog
grep -R "timeout" /var/log/


---

## 🐧 11. Linux Scripting Essentials

### Create Script

bash
nano script.sh


Example:

bash
#!/bin/bash
echo "Server: $(hostname)"


Make executable:

bash
chmod +x script.sh


---

## 📚 12. Useful Linux Tools for DevOps

| Tool          | Use                        |
| ------------- | -------------------------- |
| htop        | Process monitoring         |
| iotop       | Disk I/O monitoring        |
| iftop       | Network traffic monitoring |
| ncdu        | Disk usage explorer        |
| tmux        | Terminal multiplexer       |
| rsync       | Sync files & backups       |
| logrotate   | Log rotation               |
| cron        | Task scheduling            |
| ssh-copy-id | Copy SSH keys              |

---

## 💡 13. Linux Kernel & Boot Basics

### Check Kernel Modules

bash
lsmod


### Boot Loader (GRUB)

Config file:


/etc/default/grub


Rebuild grub:

bash
update-grub


---

## 🧩 14. SELinux (CentOS/RHEL)

Check status:

bash
sestatus


Set permissive:

bash
sudo setenforce 0


Disable (permanent):

bash
nano /etc/selinux/config
SELINUX=disabled


---

## 📦 15. Environment Variables

### List Variables

bash
env


### Set Variable

bash
export APP_ENV=prod


### Permanent Variable

Add to:

```
~/.bashrc
