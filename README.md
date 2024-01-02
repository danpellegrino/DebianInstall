# DebianInstall

This repository contains scripts to automate the installation of Debian using debootstrap, along with partitioning the disk according to specific requirements.

## Disk Setup

The script automates disk partitioning and formatting as follows:

### GPT Label

The disk will be initialized with a GUID Partition Table (GPT) label.

### Partitions

1. **EFI Partition (512MB):** This partition is designated for EFI system files.
2. **Boot Partition (1GB):** Reserved for boot files.
3. **BTRFS Partition (Remaining space):** The remainder of the disk will be allocated to a BTRFS filesystem.

### BTRFS Subvolumes

The BTRFS filesystem will have the following subvolumes:

| Subvolumes | Location | Description |
| --- | --- | --- |
| **root** | `/` | The root directory. |
| **snapshots** | `/.snapshots/` | Snapshots of the root filesystem. |
| **home** | `/home/` | User home directories. |
| **root** | `/root/` | Reserved space for the root user. |
| **log** | `/var/log/` | Logs directory. |
| **AccountsService** | `/var/lib/AccountsService/` | Configuration files for accounts. |
| **gdm** | `/var/lib/gdm3/` | Configuration files for GNOME Display Manager. |
| **tmp** | `/tmp/` | Temporary files directory. |
| **opt** | `/opt/` | Optional software packages. |
| **images** | `/var/lib/libvirt/images/` | Storage for images. |
| **containers** | `/var/lib/containers/` | Storage for containers. |
