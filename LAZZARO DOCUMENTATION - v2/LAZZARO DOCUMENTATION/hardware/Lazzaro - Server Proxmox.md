# Proxmox VE Host

#verified

## Hardware

| Component | Detail                    |
| --------- | ------------------------- |
| CPU       | Intel Core i5-10400       |
| RAM       | 32 GB                     |
| Storage   | Currently 240 + ext 512   |
| NIC       | nic0 (physical, on vmbr0) |

## OS

|               |                                           |
| ------------- | ----------------------------------------- |
| OS            | Proxmox VE 9.1                            |
| Management UI | https://<IP_ADDRESS>:8006                |
| Credentials   | user: <USERNAME> / password: **** |

## Network bridges

| Bridge | Role | IP | Physical NIC | Notes |
|--------|------|----|--------------|-------|
| vmbr0 | Management — carries Proxmox WebUI traffic | <IP_ADDRESS>/24 | nic0 | gateway <IP_ADDRESS> |
| vmbr1 | Isolated internal lab network | none | none | no gateway, no physical NIC |

> [!info] Future bridges
> **Additional bridges (vmbr2+) may be added as the lab network evolves.**

## VM inventory

| VMID | Name           | Role              | Status    |
| ---- | -------------- | ----------------- | --------- |
| ___  | OPNsense       | Firewall / router | Running   |
| ___  | Kali Linux     | Red Team          | ISO ready |
| ___  | Security Onion | Blue Team / SOC   | ISO ready |
| ___  | Metasploitable | Vulnerable target | ISO ready |
| ___  | REMnux         | Malware analysis  | ISO ready |

## Useful commands

```bash
# list all VMs
qm list

# start / stop a VM
qm start <vmid>
qm stop <vmid>

# show network interfaces on host
ip a

# show bridge status
brctl show
```


# OTHER COMMANDS:
[[10_Homelab/DOCUMENTATIONS/LAZZARO PROXMOX SERVER/LAZZARO DOCUMENTATION-v1/commands/Lazzaro - Server]]  