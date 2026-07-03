# Security Onion

#todo

## General

| | |
|-|-|
| VMID | ___ |
| OS | Security Onion ___ |
| CPU | ___ vCPU |
| RAM | ___ GB |
| Disk | ___ GB |
| ISO | ___ |

## Credentials

| | |
|-|-|
| Web UI | https://192.168.5.___ |
| Admin user | ___ |
| Admin password | ___ |

## Network

| Interface | Bridge | IP | Role |
|-----------|--------|----|------|
| eth0 | vmbr1 | 192.168.5.___ / 24 | Management |
| eth1 | vmbr1 | — | Monitoring / span port |

## Role

Blue Team / SOC — network monitoring, IDS/IPS, log analysis, alert triage across the lab network.

## Status

> [!note] ISO ready — not yet installed

## Planned usage

- [ ] Full packet capture on lab segment
- [ ] Suricata IDS rules tuning
- [ ] Zeek log analysis
- [ ] Kibana / Dashboards for alert review
- [ ] Incident response exercises against Kali attacks
