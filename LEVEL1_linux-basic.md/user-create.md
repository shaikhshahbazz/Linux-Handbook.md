## 📌 1. User & Group Management

### *Create Developer Users*

```bash
sudo adduser devuser1
sudo adduser devuser2
```

### *Create Groups*

```bash
sudo groupadd dev
sudo groupadd ops
```

### *Add Users to Groups*

```bash
sudo usermod -aG dev devuser1
sudo usermod -aG ops devuser2
```

### *Configure Default Shells*

```bash
sudo usermod --shell /bin/bash devuser1
sudo usermod --shell /bin/zsh devuser2
```

### *Set Default Permissions for Home*

```bash
sudo chmod 750 /home/devuser1
```

### *Disable or Lock Unused Accounts*

```bash
sudo usermod --lock olduser
# Disable login shell
sudo usermod -s /usr/sbin/nologin olduser
```

---
