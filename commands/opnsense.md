# OPNsense — Command Cheat Sheet

#wip

## Shell access

Access via Proxmox console or SSH (once WAN is resolved).

## Network diagnostics

```bash
ifconfig                       # show all interfaces
ifconfig vtnet0                # show WAN interface
ifconfig vtnet1                # show LAN interface
netstat -rn                    # show routing table
ping <IP_ADDRESS>               # ping Cisco gateway
ping <IP_ADDRESS>                   # ping internet (when WAN works)
```

## DHCP client

```bash
dhclient vtnet0                # manually request DHCP on WAN
kill $(cat /var/run/dhclient.vtnet0.pid)  # kill DHCP client
```

## DNS

```bash
cat /etc/resolv.conf           # current DNS config
host google.com                # DNS resolution test
```

## Logs

```bash
clog /var/log/system.log       # system log
clog /var/log/filter.log       # firewall filter log
```

## Services

```bash
/usr/local/etc/rc.d/opnsense-monit.sh restart   # restart monitoring
pluginctl -s dnsmasq restart                     # restart DNS
```
