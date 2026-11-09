# Troubleshooting — OPNsense WAN no DHCP IP

#open
___
## Problem

OPNsense `vtnet0` (WAN interface, connected to vmbr0) is not receiving a DHCP IP address from the Cisco 1921 (<IP_ADDRESS>).

## Environment

|                        |                                        |
| ---------------------- | -------------------------------------- |
| OPNsense WAN interface | vtnet0                                 |
| Expected DHCP server   | Cisco 1921 — <IP_ADDRESS>               |
| Proxmox bridge         | vmbr0 (nic0, carries home LAN traffic) |
| Expected IP range      | 192.168.2.x/24                         |

## Steps already tried


_____

## Current workaround

WAN functionality is currently not used. Internet access for the lab is provided via the ISP modem directly. OPNsense LAN (vtnet1 → <IP_ADDRESS>/24) is operational.

## Hypotheses

- DHCP not enabled on Cisco 1921 GigabitEthernet0/1
- vmbr0 not correctly bridging traffic between vtnet0 and nic0
- OPNsense vtnet0 not set to DHCP client (check via shell: `ifconfig vtnet0`)
- MAC address filtering on Cisco side

## Next steps to try

- [ ] Verify DHCP pool on Cisco 1921: `show running-config | include dhcp`
- [ ] Check vtnet0 gets a DHCP lease manually: `dhclient vtnet0`
- [ ] Capture traffic on Proxmox host: `tcpdump -i vmbr0 port 67 or port 68`
- [ ] Verify vmbr0 bridge includes nic0: `brctl show vmbr0`

## Resolution

> Not yet resolved.


____


16/04/2026 00:01
# OPNsense Troubleshooting

## Network Architecture Modifications

The setup follows a virtual kind-of "Router-on-a-stick" model, isolating external traffic from the internal network through Linux bridges.

- **WAN (vmbr0):** Attached to the physical Ethernet port. Configured as <IP_ADDRESS>/24 
- **LAN (vmbr1):** An isolated bridge (no physical ports) dedicated to internal VM-to-VM communication. IP <IP_ADDRESS>/24.

## Configuration Steps (OPNsense Console)

1. Interface Assignment (Option 1)

The virtual drivers were manually mapped to the respective bridges:

- **WAN:** Mapped to `vtnet0` (linked to `vmbr0`).
- **LAN:** Mapped to `vtnet1` (linked to `vmbr1`).
- _Note:_ LAGGs and VLANs were skipped to maintain a flat network structure.

2. IP Configuration (Option 2)

- **LAN Static IP:** `<IP_ADDRESS>/24`   (ONLY LAN FOR NOW)
- **DHCP Server:** Enabled
- **Range:** `<IP_ADDRESS>` - `<IP_ADDRESS>`
- **IPv6:** Disabled to prevent routing complexities during initial setup.

## Troubleshooting & Resolutions

- **Initial Issue:** OPNsense correctly accepted and displayed the exact WAN and LAN IP configuration, but the WebGUI could not be reached despite the interfaces being configured as expected.
- **Root Cause:** The VM was running the live/non-installed version of OPNsense rather than an installed operating system instance.
- **Resolution:** The issue was resolved by completing the OPNsense installation on the VM and booting from the installed system. After installation, the WebGUI became accessible normally.
- **Network Observation:** The Cisco router was not assigning a dynamic IP address to `vmbr0`. The bridge consistently used `<IP_ADDRESS>`, which was the same IP address assigned to the physical network interface of the Proxmox server.

## Summary Table

| Component          | Setting         | Value                            |
| ------------------ | --------------- | -------------------------------- |
| **WAN Interface**  | Bridge / IP     | `vmbr0` / `<IP_ADDRESS>`          |
| **LAN Interface**  | Bridge / IP     | `vmbr1` / `<IP_ADDRESS>`          |
| **LAN DHCP Range** | Pool            | `<IP_ADDRESS> - .159`           |
| **Client VM IP**   | Static Test IP  | `<IP_ADDRESS>`                   |
| **Proxmox NIC**    | Firewall Flag   | **Disabled**                     |
| **Access URL**     | WebGUI Opnsense | `https://<IP_ADDRESS>` /(SUCCESS) |
Everything is currently working, the issue was that the vm was not installed and was not running as installed OS, but on the "trial" version. 

## Errors committed:
- OPNsense was used before completing the installation on the VM.
- The assumption that the WebGUI issue was caused by interface configuration was incorrect; WAN and LAN addressing were already configured correctly.
- `vmbr0` was not receiving a dynamic address from the Cisco router and remained fixed at `<IP_ADDRESS>`, matching the Proxmox server NIC.
- Previous documentation incorrectly stated that the Cisco router was providing DHCP leases to this segment.

___
