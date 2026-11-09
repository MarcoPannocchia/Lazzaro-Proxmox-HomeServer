# Cisco 1841 — Router A

#todo

## Status

> [!warning] Not yet integrated
> This device has not been configured. Factory defaults, untouched.

## Hardware

| Component         | Detail     |
| ----------------- | ---------- |
| Model             | Cisco 1841 |
| OS version        | xx         |
| Modules           | None       |
| Management access | Console    |

## Planned role

___ (e.g. inter-VLAN routing, WAN simulation, BGP/OSPF lab with 1841-B)

## Credentials

|                 |        |
| --------------- | ------ |
| Hostname        | panno  |
| Enable password | ciccio |
| SSH user        | ___    |
| SSH password    | ___    |

## Interface map

| Interface          | Description | IP  | Role |
| ------------------ | ----------- | --- | ---- |
| GigabitEthernet0/0 | ___         | ___ | ___  |
| GigabirEthernet0/1 | ___         | ___ | ___  |

---

## Configuration commands

> [!note]
> To be filled in when device is integrated into the lab. **Currently not in use**

### Interfaces

```ios
interface FastEthernet0/0
 description ___
 ip address ___.___.___.___  ___.___.___.___ 
 no shutdown

interface FastEthernet0/1
 description ___
 ip address ___.___.___.___  ___.___.___.___
 no shutdown
```

### Static routes

```ios
ip route <IP_ADDRESS> <IP_ADDRESS> ___.___.___.___ ! default route
ip route ___.___.___.___  ___.___.___.___  ___.___.___.___
```

### Save configuration

```ios
copy running-config startup-config
```

---

> [!info] Link
> See also [[10_Homelab/DOCUMENTATIONS/LAZZARO PROXMOX SERVER/LAZZARO DOCUMENTATION - v2/LAZZARO DOCUMENTATION/hardware/cisco-1841-B]] — the two routers are intended to work together.
