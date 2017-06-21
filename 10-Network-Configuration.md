## ifcfg-eth0
* BOOTPROTO=none, verlangt: IPADDR, GATEWAY, PREFIX
* Doku: /usr/share/doc/iniscripts-*/sysconfig.txt
* Zusätzliche IP-Adresse auf einem Interface mit IPADDR0,GATEWAY0,PREFIX0[,IPADDR1,GATEWAY1,GATEWAY2]

## Namensauflösung
* Reihenfolge der Namensauflösungen wird in /etc/nsswitch.conf gesetzt Parameter: hosts
* Best Practice: wichtigste Server sollen hier drinnen stehen
* Commandos: dig und host arbeiten nur mit der resolv.conf

## Device Naming Schema
* ethX => Ethernet (old)
* en____ => EtherNet (new)
* eno___ => onboard Device
* ens___ => PCI Express
* enp___ => PCI Slot
* Mapping der Devices zu den Interfaces
````
[kiosk@foundation2 network-scripts]$ lspci | grep Ethernet
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
01:05.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)
# Hex number 00:19.0 => 0s25 in Dezimal
[kiosk@foundation2 network-scripts]$ ip addr | grep enp
2: enp0s25: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UP qlen 1000
3: enp1s5: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000

# HW und Treiber Einstellungen für Netzwerkinterface
[kiosk@foundation2 network-scripts]$ ethtool enp0s25
````

## Network Manager (new in RHEL7)
* nmcli (incl. package bash-completion!!!)

## Hostnamen statisch setzen
hostnamectl

## Network Connections
netstat (old), ss (new)
