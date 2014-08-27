# SmartOS

* [SmartOS](http://smartos.org/) - SmartOS unites four extraordinary technologies to revolutionize the datacenter:
ZFS, DTrace, Zones, KVM
* [Project FIFo](https://project-fifo.net/) - Private Cloud Lösung


## Howto
* [Resizing Linux VM Disks](http://wiki.smartos.org/display/DOC/Resizing+Linux+VM+Disks)
* [pfSense on SmartOS KVM Zone](http://nullworks.wordpress.com/2013/12/19/pfsense-on-smartos-kvm-zone/) - pfSense von einem ISO in eine KVM auf SmartOS installieren
* [Tips for node.js Deployment on SmartOS](http://marius.me.uk/blog/2013/04/tips-nodejs-deployment-smartos/)

## Project Fifo

* [Upgrade Guide](https://docs.project-fifo.net/general/upgrade.html)


## Befehle

### Netzwerk

> alle virtuellen netzwerke anzeigen:
```bash
dladm show-vnic
```

---
> Den Abschnitt "Network Interfaces" aus sysinfo als json ausgeben:
```bash
sysinfo | json "Network Interfaces"
```

---
> überprüfen welche Pakete an eine bestimmte IP-Adresse des Servers gesendet werden:
```bash
snoop 10.1.0.2
```

---
> create a tun0 device
```bash
ifconfig ip.tun0 plumb
```


---

#### ipv6

> Ein device mit ipv6 unterstützung anlegen
```bash
ifconfig rge0 inet6 plumb
```
> Das device mit einer ipv6 adresse starten
```bash
ifconfig rge0 inet6 addif 2a01:4f8:110:5101::1/64 up
```
> Eine Route für diese ipv6 adresse setzen
```bash
route add -inet6 fe80::1 2a01:4f8:110:5101::1 -interface
```
> Abschließend eine ipv6 default route setzen
```bash
route add -inet6 default fe80::1
```
> Weitere Adressen hinzufügen
```bash
ifconfig rge0 inet6 addif 2a01:4f8:110:5101::2 up
ifconfig rge0 inet6 addif 2a01:4f8:110:5101::3 up
```
> Anderer Weg um neue Adressen hinzuzufügen:
```bash
ifconfig net1 inet6 addif 2a01:4f8:110:5101:dead:beef:1000:1001/128 up
ifconfig net1 inet6 addif 2a01:4f8:110:5101:dead:beef:1000:1002/128 up
ifconfig net1 inet6 addif 2a01:4f8:110:5101:dead:beef:1000:1003/128 up
ifconfig net1 inet6 addif 2a01:4f8:110:5101:dead:beef:1000:1004/128 up
```
> Alternative mit ipadm:
```bash
ipadm create-addr -t -T addrconf rge0/v6a
ipadm create-addr -t -T static -a 2a01:4f8:a0:13c8::2/64 rge0/v6s
```
> Allow ip snoofing for ipv6 device
```bash
echo '{"update_nics": [{"mac": "b2:1e:ba:a5:6e:71", "allow_ip_spoofing": true}]}' | vmadm update e5c4e68f-9b21-4d46-9c12-1e870b05e470
```
> see: http://www.zomo.co.uk/2013/08/ipv6-for-smartos-guest-vms-on-hetzner-hosts/

---


### System

> Informationen der CPU ausgeben lassen:
```bash
prtdiag
```

----
### ZSF / ZPOOL

> ein Volume erzeugen:
```bash
zfs create -o casesensitivity=mixed daten/virtual/KVM
```

---
> ein 10GB großes Volume erzeugen:
```bash
zfs create -p -V 10G daten/virtual/KVM/debian/disk0
```

---
> ein zpool für eine zone freigeben:
```bash
zonecfg -z a30e0d01-2902-4c83-a960-e7ca92be0abe 'add dataset; set name="zones/daten"; end; verify; commit'
```

----
### Zones

> eine zone mit config starten:
```bash
vmadm create -f test_vm1.json
```

----
### Sonstiges

> befehl als root role ausführen:
```bash
pfexec befehl
```

----