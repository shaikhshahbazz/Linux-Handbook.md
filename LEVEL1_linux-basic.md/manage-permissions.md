````md
# 📌 Manage Permissions for Project Directories

This section explains how to set ownership, groups, and permissions for project folders in Linux using Git Bash or any Linux terminal.


## 🗂️ 1. Create Project Directory

```bash
sudo mkdir -p /opt/project-app
```

## 👤 2. Set Owner of the Directory

Assign a specific user as the owner:

```bash
sudo chown devuser1 /opt/project-app
```

## 👥 3. Set Group Ownership

Assign a group to the directory:

```bash
sudo chgrp dev /opt/project-app
```

Add users to the group if needed:

```bash
sudo usermod -aG dev devuser1
sudo usermod -aG dev devuser2
```

## 🔐 4. Set Directory Permissions

### ✔ Grant read, write, execute to owner

### ✔ Grant read & execute to group

### ✔ Grant read & execute to others

```bash
sudo chmod 755 /opt/project-app
```
