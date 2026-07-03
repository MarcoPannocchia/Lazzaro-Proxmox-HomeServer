# OPNsense VM

#wip

## General

| Components | Information   |
| ---------- | ------------- |
| VMID       | 100           |
| OS         | OPNsense 26.1 |
| CPU        | 2vCPU         |
| RAM        | 2 GB          |
| Disk       | 32 GB         |

## Credentials

|                         |                                          |
| ----------------------- | ---------------------------------------- |
| Web UI                  | https://<IP_ADDRESS>                      |
| Admin user              | `root`                                   |
| Admin password          | opnsense (Still the same for now)        |
| First login (installer) | user: <USERNAME> / password: `opnsense` |

## Network interfaces

| Interface | Bridge | Role                  | IP              | Status |
| --------- | ------ | --------------------- | --------------- | ------ |
| vtnet0    | vmbr0  | WAN — from Cisco 1921 | 192.168..2.1/24 | UP     |
| vtnet1    | vmbr1  | LAN — lab internal    | <IP_ADDRESS>/24  | UP     |

## Current configuration

WAN and LAN is currentlyn use —  not working filters and necessity for additional configuration


## Planned configuration

- [x] Resolve WAN DHCP issue
- [ ] Define firewall rules per VLAN/domain
- [ ] Configure DNS resolver
- [ ] Configure DHCP server for internal segments
