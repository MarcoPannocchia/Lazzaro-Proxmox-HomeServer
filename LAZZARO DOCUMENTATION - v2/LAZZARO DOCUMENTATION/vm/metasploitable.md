# Metasploitable

#todo

## General

| | |
|-|-|
| VMID | ___ |
| OS | Metasploitable 2 / 3 ___ |
| CPU | ___ vCPU |
| RAM | ___ GB |
| Disk | ___ GB |
| ISO | ___ |

## Credentials

| | |
|-|-|
| Default user | `msfadmin` |
| Default password | `msfadmin` |

> [!warning] Intentionally vulnerable
> This VM must never be exposed outside vmbr1. Keep it isolated on the internal lab network at all times.

## Network

| Interface | Bridge | IP | Role |
|-----------|--------|----|------|
| eth0 | vmbr1 | 192.168.5.___ / 24 | Lab internal only |

## Role

Intentionally vulnerable target for Red Team exercises originating from Kali Linux. Monitored by Security Onion.

## Status

> [!note] ISO ready — not yet installed

## Known vulnerabilities (reference)

- VSFTPd 2.3.4 backdoor
- Samba usermap_script
- UnrealIRCd backdoor
- Weak SSH credentials
- Multiple web application vulns (DVWA, Tikiwiki, etc.)
