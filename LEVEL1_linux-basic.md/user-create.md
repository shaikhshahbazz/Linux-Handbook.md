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

