# VPS-debian11

Interactive multi-VM manager for Google IDX and Linux hosts using QEMU/KVM + cloud images.

## What this project does

This repository provides `vps.sh`, a menu-driven Bash script to:

- Create VMs from cloud images
- Start and stop VMs
- Edit VM settings (hostname, user, password, SSH port, RAM, CPU, GUI mode, port forwards)
- Resize VM disk images
- Show VM information and basic performance stats
- Delete VMs safely with confirmation

## Supported guest OS images

- Ubuntu 22.04
- Ubuntu 24.04
- Debian 11
- Debian 12
- Fedora 40
- CentOS Stream 9
- AlmaLinux 9
- Rocky Linux 9

## Quick start (Google IDX)

1. Open Google IDX: https://idx.google.com/
2. Import this repository:
   - https://github.com/SHASHIKA-M/VPS--IDX
3. Run:

```bash
chmod +x vps.sh
./vps.sh
```

Or run directly from GitHub:

```bash
bash <(curl -fsSL https://raw.githubusercontent.com/SHASHIKA-M/VPS--IDX/main/vps.sh)
```

## Quick start (local Linux)

Install dependencies (Debian/Ubuntu example):

```bash
sudo apt update
sudo apt install -y qemu-system-x86 qemu-utils cloud-image-utils wget openssl
```

Then run:

```bash
chmod +x vps.sh
./vps.sh
```

## VM storage

By default, VM files are stored in:

```bash
$HOME/vms
```

For each VM, the script keeps:

- `<vm-name>.conf` (configuration)
- `<vm-name>.img` (disk image)
- `<vm-name>-seed.iso` (cloud-init seed)

To use a custom directory:

```bash
VM_DIR=/path/to/vms ./vps.sh
```

## SSH access

After starting a VM, connect with:

```bash
ssh -p <ssh_port> <username>@localhost
```

Use the password you configured during VM creation.

## Notes

- Hardware virtualization must be available for best performance (`-enable-kvm`).
- VM credentials are saved in the VM config file for management convenience.
- If a chosen SSH port is already in use, the script asks for another port.
