# README

Environment is currently on production

Minor change may occur infrequently

Login to any VM with Termius or with this credential

```
user: user
pass: admin
```

## Current Running VMs

>> Do not shut down any node. If you really need to do so, please consult with the system administrator via email to <syafa@syafahadyan.com>

>> Do not shut down any VM with `no-shutdown` tag. Doing so may affect the integrity of the cluster and access to the web interface might not be possible. If you really need to do so, please consult with the system administrator via email to <syafa@syafahadyan.com>

|VMID|Name|Role|Note|
|:---|:---|:---|:---|
|200|iriguchi|nginx|DO NOT SHUT DOWN THIS VM|
|201|morata|linux-mirror|DO NOT SHUT DOWN THIS VM|
|202|sesshoku|subnet-router|DO NOT SHUT DOWN THIS VM|
|203|teikyo|minecraft-java-server|Private usage|
|204|shiten|subnet-router,exit-node|DO NOT SHUT DOWN THIS VM|
|205|kanshi|to-be-defined|To be defined|
|206|fukusha|syncthing|Private usage|
|1000|hitori|kubernetes-control-plane|Testing phase|
|1001|futari|kubernetes-worker|Testing phase|
|1002|hikari|kubernetes-worker|Testing phase|
|2000|tsubaki|atr-backend|Production|
|2001|ajisai|atr-backend|Production|
|2002|suisen|atr-backend|Production|
|2003|nadeshiko|atr-backend|Production|
|2004|sumire|atr-backend|Production|
|2005|tsutsuji|atr-backend|Production|
|2006|nanohana|atr-backend|Staging|
|2007|kinmokusei|atr-backend|Staging|
|3000|terraform-0|atr-backend_terraform|Testing phase|
|3001|terraform-1|atr-backend_terraform|Testing phase|
|3002|terraform-2|atr-backend_terraform|Testing phase|

## Templates

Format:

`node_vmid_template`

Template Format:

`distro-bios-type`

>> Use `washi_103_debian-uefi` for standard default

- washi_100_debian-seabios (***deprecated, do not use this in production environment***)
- washi_101_debian-uefi (***deprecated, do not use this in production environment***)
- washi_102_arch-linux-uefi
- washi_103_debian-uefi

### Template Creation Guide

#### General

- VM ID: (100 - 199)
- Name: `distro-bios`

#### System

- Machine: q35
- BIOS: OVMF (UEFI)
- EFI Storage: local-lvm
- Pre-Enroll keys: false
- SCSI Controller: VirtIO SCSI Single
- Qemu Agent: true
- Add TPM: false

#### Disks

- Storage: local-lvm

#### CPU

- CPU Model: Host
- CPU Vendor: Host

#### Memory

- Ballooning Device: set to `true` for dinamically extendable memory, otherwise set to `false`

#### Network

- Bridge: vmbr0
- VLAN Tag: no VLAN
- Firewall: true
- Model: VirtIO (paravirtualized)
- MAC address: auto

## VM Migration Guide

Remove CD/DVD ISO from the VM before doing migration
