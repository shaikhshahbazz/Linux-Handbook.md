````md
# 📌 LVM Setup for Storage Scaling
````
Logical Volume Manager (LVM) allows you to manage disk storage flexibly.  
You can extend partitions, add new disks, and resize filesystems easily using LVM.

This section covers the full step-by-step LVM setup process.

---

## 🧩 1. Install LVM Tools (if not installed)

```bash
sudo apt install lvm2 -y
````

Check LVM installation:

```bash
sudo pvdisplay
```

## 💽 2. Identify the New Disk

List available disks:

```bash
lsblk
```

Example:
Your new disk might appear as `/dev/xvdb` or `/dev/sdb`.

## 🟦 3. Create a Physical Volume (PV)

```bash
sudo pvcreate /dev/sdb
```

Verify:

```bash
sudo pvdisplay
```

## 🟩 4. Create a Volume Group (VG)

Create a VG named `vgdata`:

```bash
sudo vgcreate vgdata /dev/sdb
```

Check VG:

```bash
sudo vgdisplay
```

## 🟧 5. Create a Logical Volume (LV)

Create a 10GB LV named `lvdata`:

```bash
sudo lvcreate -L 10G -n lvdata vgdata
```

OR create LV using all space:

```bash
sudo lvcreate -l 100%FREE -n lvdata vgdata
```

Check LV:

```bash
sudo lvdisplay
```

## 📁 6. Format the Logical Volume

Format LV with ext4 filesystem:

```bash
sudo mkfs.ext4 /dev/vgdata/lvdata
```

## 📂 7. Mount the Logical Volume

Create mount directory:

```bash
sudo mkdir /data
```

Mount LV:

```bash
sudo mount /dev/vgdata/lvdata /data
```

Verify:

```bash
df -h
```

## 🔄 8. Make the Mount Permanent (fstab)

Add entry to `/etc/fstab`:

```bash
/dev/vgdata/lvdata   /data   ext4   defaults   0 0
```

Reload fstab:

```bash
sudo mount -a
```

# 🚀 LVM Storage Scaling (Extend Storage)

Below is how you increase LV size when disk becomes full.

## 🧩 9. Add a New Disk to Volume Group

```bash
sudo pvcreate /dev/sdc
sudo vgextend vgdata /dev/sdc
```

Check:

```bash
sudo vgdisplay
```

## 🔧 10. Extend the Logical Volume

Extend LV by 10GB:

```bash
sudo lvextend -L +10G /dev/vgdata/lvdata
```

OR extend to all free space:

```bash
sudo lvextend -l +100%FREE /dev/vgdata/lvdata
```

## 📌 11. Resize the Filesystem

For EXT4:

```bash
sudo resize2fs /dev/vgdata/lvdata
```

For XFS:

```bash
sudo xfs_growfs /data
```
