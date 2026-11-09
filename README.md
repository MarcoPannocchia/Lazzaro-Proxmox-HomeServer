<div align="center">

<img src="assets/banner.png" alt="Lazzaro Proxmox HomeServer" width="100%">

# Lazzaro — Proxmox Home Cybersecurity Lab

**Documentation of a home cybersecurity lab built around a Proxmox VE host, a Cisco edge router and an OPNsense firewall.**

[![Instagram](https://img.shields.io/badge/Instagram-@marco__pannocchia-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](https://www.instagram.com/marco_pannocchia/)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Marco_Pannocchia-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/marco-pannocchia-191924433/)

![Proxmox VE](https://img.shields.io/badge/Proxmox_VE-9.1-E57000?style=flat-square&logo=proxmox&logoColor=white)
![OPNsense](https://img.shields.io/badge/OPNsense-26.1-D94F00?style=flat-square)
![Cisco](https://img.shields.io/badge/Cisco-1921-1BA0D7?style=flat-square&logo=cisco&logoColor=white)
![Docs](https://img.shields.io/badge/status-documentation_archive-lightgrey?style=flat-square)

</div>

---

## About

Lazzaro is the name of the Proxmox host at the center of this lab; **ICARO** is the Cisco 1921 router in front of it. The goal was a realistic, isolated environment to practice red team, blue team and malware analysis, with a controlled gateway between the lab and the home network.

This repository holds the documentation only: hardware, network design, VM notes, command references and troubleshooting logs.

## Architecture

```
Internet ── Wind modem ── ICARO (Cisco 1921) ── Home LAN ── Lazzaro (Proxmox, vmbr0)
                                                                 │
                                                          OPNsense VM (WAN)
                                                                 │
                                                       vmbr1 (isolated lab LAN)
                                                                 │
                                         Kali · Security Onion · Metasploitable · REMnux
```

- **vmbr0** carries Proxmox management and the OPNsense WAN path.
- **vmbr1** has no physical NIC: lab traffic never touches the home network, and OPNsense is the only gateway between the two.
- The Cisco 1921 uses a static default route to the modem, which does not support dynamic routing.

Details and design decisions: [`network/topology.md`](network/topology.md).

## Repository layout

| Folder | Content |
| --- | --- |
| [`hardware/`](hardware) | Proxmox host, Cisco 1921 (ICARO), Cisco 1841 A and B |
| [`network/`](network) | Topology, bridges, subnets, architectural decisions |
| [`vm/`](vm) | OPNsense, Kali Linux, Security Onion, Metasploitable, REMnux |
| [`commands/`](commands) | Command references for ICARO, Lazzaro and OPNsense |
| [`troubleshooting/`](troubleshooting) | Problem logs, e.g. [OPNsense WAN without DHCP](troubleshooting/opnsense-wan-dhcp.md) |

## The lab

| Component | Detail |
| --- | --- |
| Host | Intel Core i5-10400, 32 GB RAM, Proxmox VE 9.1 |
| Edge router | Cisco ISR 1921 ("ICARO") |
| Firewall | OPNsense 26.1 (VM, 2 vCPU, 2 GB RAM) |
| Red team | Kali Linux |
| Blue team / SOC | Security Onion |
| Vulnerable target | Metasploitable |
| Malware analysis | REMnux |

## Status

Documentation archive. The hardware has been decommissioned, and the VM pages for Kali, Security Onion, Metasploitable and REMnux are templates that were never filled in. Pages carry status tags: `#verified`, `#wip`, `#todo`, `#open`. IP addresses are replaced by placeholders (`<IP_ADDRESS>`, `___`).

The notes are written in Obsidian-flavored Markdown.

## Connect

- Instagram: [@marco_pannocchia](https://www.instagram.com/marco_pannocchia/)
- LinkedIn: [Marco Pannocchia](https://www.linkedin.com/in/marco-pannocchia-191924433/)

## License

[CC0 1.0 Universal](LICENSE)
