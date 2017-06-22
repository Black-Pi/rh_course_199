## Suchen von Konfigurationsfiles
1. /usr/lib/<service> => Pakete => Priorität 3
2. /run/<service> => manuelle Änderungen nur währen der Laufzeit (bis zum nächsten Reboot) => Priorität 2
3. /etc/<service> => manuelle Änderungen - ergänzend zu /usr/lib/<service> => Priorität 1
* Bei Verwendung gleicher Dateinamen unter etc und usr wird das Konfigurationsfile unter usr ignoriert


## Änderungen bei Konfigurationsfiles nach Update
* Wenn Änderungen "egal" sind wird ein File angelegt mit /etc/samba/smb.conf.rpmnew
* Wenn neue Parameter von der neuen Version des Pakets in einem Konfigurationsfile benötigt werden wird die manuell geänderte auf .rpmsave File angelegt: /etc/smba/smb.conf.rpmsave
* rpmconf.noarch (EPEP Repo) um rpmnew und rpmsave Dateien zu suchen und hineinzumergen (wird allerdings nicht von RedHat unterstützt)

## systemd
* Hält Beschreibunsdateien
* Directory: /usr/lib/systemd/system
* Kann als crond und fstab fungieren
* Laufende Services abfragen: `systemctl list-units --type service`
````
systemctl list-dependencies multi-user.target
systemctl list-unit --type target
````

## Prozesse in []
sind Kernel Prozesse

## systemd System-Files abändern
````
mkdir /etc/systemd/system/sladp.service.d
cp /usr/lib/systemd/system/slapd.service /etc/systemd/system/sladp.service.d/new-filename.conf
# Änderungen durchführen beim new-filename.conf
systemctl daemon-reload
systemctl restart sldap.service
# beide Konfigurationsfiles ziehen
````
* Mapping der Targets auf runlevels `ls -l /usr/lib/systemd/system/runlevel*.target`

## Booten
* maintenance => vor rc.sysinit => keine filesysteme gemountet, kein daemon, root / ro
* single user => nach rc.sysinti => /etc/fstab, / rw, udev daemon für devices
* maintenance => emergency
* singel user => rescue

* Single-User Mode / Emergency Mode: unter linux16 `systemd.unit=rescue.target` bzw. `s` oder `systemd.unit=rescue.emergency` am Ende der Zeile, anschließend Ctrl-X to start
* "Einbrechen": unter linux16 `rd.break` am Ende der Zeile, anschließend Ctrl-X to start
````
# / Filesystem ist unter /sysroot gemountet
mount -o rw,remount /sysroot
chroot /sysroot
passwd ...
# /etc/shadow Datei hat falsche SELinux Labels, daher
## Variante 1: relabelling aller Files am Filesystem
touch /.autorelabel
## Variante 2: SELinux Policys setzen
load_policy -i
restorecon -v /etc/shadow
#Entweder: `setenforce 0 && exit && systemctl default` oder `reboot`
# nach dem booten: setenforce 1 setzen, falls setenforce 0 ist
````

## grub2
* /boot/grub2/grubenv => Default Kernel
* Default-Kernel: grub2-set-default 'Title'
* Title wird in /etc/grub2.cfg unter ^menuentries definiert
* grub2 Änderungen im File `/etc/default/grub` und persistieren: `grub2-mkconfig > /boot/grub2/grub2.cfg`

