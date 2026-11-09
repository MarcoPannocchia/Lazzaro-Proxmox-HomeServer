# Proxmox — Command Cheat Sheet

#verified

## VM management

```bash
qm list                        # list all VMs and status
qm start <vmid>                # start a VM
qm stop <vmid>                 # stop a VM (hard)
qm shutdown <vmid>             # graceful shutdown
qm reset <vmid>                # reset a VM
qm status <vmid>               # show VM status
qm config <vmid>               # show VM configuration
```

## Snapshots

```bash
qm snapshot <vmid> <name>      # create snapshot
qm listsnapshot <vmid>         # list snapshots
qm rollback <vmid> <name>      # rollback to snapshot
qm delsnapshot <vmid> <name>   # delete snapshot
```

## Network

```bash
ip a                           # show all interfaces and IPs
brctl show                     # show bridge status
ip route show                  # show routing table
```

## Storage

```bash
pvesm status                   # show storage status
pvesm list <storage>           # list content of a storage
```

## System

```bash
pveversion                     # show Proxmox version
systemctl status pve-cluster   # cluster status
journalctl -u pveproxy         # proxy logs
```
