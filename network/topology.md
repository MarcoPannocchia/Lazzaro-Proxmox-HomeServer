# Network Topology

#wip

## Current state

| Segment      | Subnet          | Gateway                    | Notes                   |
| ------------ | --------------- | -------------------------- | ----------------------- |
| Home LAN     | <IP_ADDRESS>/24* | <IP_ADDRESS> (Cisco 1921)   | Lazzaro host lives here |
| Lab internal | <IP_ADDRESS>/24  | <IP_ADDRESS> (OPNsense LAN) | Isolated via vmbr1      |
*THE IPs THAT GO FROM ==<IP_ADDRESS>   -  <IP_ADDRESS>== ARE INCLUDED IN  A INTERNAL LAN  DHCP FIREWALL BASED *CONFIGURED ON OPNSENSE**


## Bridges

| Bridge | Subnet | Gateway | Physical NIC | Purpose |
|--------|--------|---------|--------------|---------|
| vmbr0 | <IP_ADDRESS>/24 | <IP_ADDRESS> | nic0 | Proxmox management + WAN path |
| vmbr1 | — | — | none | Isolated internal lab segment |

> [!info] Future bridges
> Additional bridges will be added as the lab grows (e.g. dedicated segments per domain: red team, blue team, malware analysis).

## Architectural decisions

**Why OPNsense instead of pfSense CE?**
___

**Why vmbr1 is isolated (no physical NIC)?**
All lab VM traffic stays within Proxmox and never touches the physical home network. OPNsense acts as the controlled gateway between the two worlds. The only vmbr0 can touch the home network. Lazzaro is indeed reachable from any device within the home newtork.

**Why static route on the Cisco 1921?**
The modem Wind does not support dynamic routing. A static default route on the 1921 pointing to the modem is sufficient and more predictable.

## Future plans

- [ ] Integrate Cisco 1841-A and 1841-B for routing/VLAN lab exercises
- [ ] Define full VLAN schema across the lab
- [ ] Add dedicated bridges per security domain
- [ ] Configure OPNsense WAN (resolve DHCP issue — see [[10_Homelab/DOCUMENTATIONS/LAZZARO PROXMOX SERVER/LAZZARO DOCUMENTATION-v1/troubleshooting/opnsense-wan-dhcp]])
- [ ] Expand internal subnet plan as new VMs come online Proxmox
- [ ] Add additional security as the server will be reachable from outside the network.
