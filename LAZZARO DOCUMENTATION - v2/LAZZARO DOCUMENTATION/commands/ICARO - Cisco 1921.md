# Cisco 1921 — Command Reference

#verified 

## Interfaces

```LINUX
interface GigabitEthernet0/0
 description WAN - verso modem Wind
 ip address <IP_ADDRESS>  <IP_ADDRESS> 
 no shutdown
```

## VLANs

```LINUX
vlan 10
 name vlan 10

interface GigabitEthernet0/1/0
switchport mode access
 switchport access vlan 10
 no shutdown

interface GigabitEthernet0/1/1
 switchport mode access
 switchport access vlan 10
 no shutdown

interface Vlan10
 ip address <IP_ADDRESS>  <IP_ADDRESS> 
 no shutdown
```

## Static routes

``` LINUX
ip route <IP_ADDRESS> <IP_ADDRESS> <IP_ADDRESS> 
ip route <IP_ADDRESS>  <IP_ADDRESS>  <IP_ADDRESS>
```

## Save configuration

```LINUX
copy running-config startup-config
write memory
```

## Verification cheat sheet

```LINUX
show ip interface brief        ! all interfaces — IP and status
show ip route                  ! routing table
show running-config            ! active configuration
show startup-config            ! saved configuration
show vlan-switch               ! VLAN status on switch module
show version                   ! IOS version and installed modules
show cdp neighbors             ! connected Cisco devices
```
