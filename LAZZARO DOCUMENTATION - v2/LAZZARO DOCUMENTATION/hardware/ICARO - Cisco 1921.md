# Cisco 1921 Router

 The Chosen name for this machine is ICARO.
 
#verified



## Hardware

| Component         | Detail                                                   |
| ----------------- | -------------------------------------------------------- |
| Model             | Cisco 1921                                               |
| OS version        | xx                                                       |
| Module slot 0     | EHWIC switch module (GigabitEthernet switchport capable) |
| Module slot 0     | EHWIC switch module (GigabitEthernet switchport capable) |
| Management access | Console / Telnet or SSH                                  |

## Credentials

|                 |        |
| --------------- | ------ |
| Hostname        | panno  |
| Enable password | ciccio |
| SSH user        | panno  |
| SSH password    | ciccio |

## Interface map

| Interface            | Description                     | IP                        | Role        |
| -------------------- | ------------------------------- | ------------------------- | ----------- |
| GigabitEthernet0/0   | WAN — verso modem Wind          | <IP_ADDRESS> /24         | Uplink ISP  |
| GigabitEthernet0/1/0 | Attached to Lazzaro             | (Proxmox - <IP_ADDRESS>) | Access port |
| GigabitEthernet0/1/1 | For any device (Mainly testing) | xx                        | Access port |
| Vlan 10              | Area of Proxmox server          | 192.168.2.x /24           | SVI gateway |

---

## Configuration commands

[[10_Homelab/DOCUMENTATIONS/LAZZARO PROXMOX SERVER/LAZZARO DOCUMENTATION-v1/commands/ICARO - Cisco 1921|ICARO]]

> [!info] Future development
> VLAN schema and routing toward 1841s will expand as the lab network evolves. See [[10_Homelab/DOCUMENTATIONS/LAZZARO PROXMOX SERVER/LAZZARO DOCUMENTATION-v1/network/topology]].

