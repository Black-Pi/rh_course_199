## File Permissions werden Sequentiell abgearbeitet
1. User Permissions
2. Group Permissions
3. Others

## Berechtigungen
````
sst rwx rwx rwx ./+
421 421 421 421 ACL?

t kommt auf die Stelle vom x bei others; kleines t bedeutet incl. x, großes T ohne x
2. s kommt auf die Stelle vom x bei group, kleines s beduete incl. x, großes S ohne x
1. s kommt auf die Stelle vom x bei user
````

## Sticky Bit (t)
* Wird dauf Verzeichnisse gesetzt: Nur der Eigentümer und root darf in diesem Verzeichnis Dateien umbenennen und/oder löschen
* Grund: user ist in gruppe des Verzeichnisses drinnen und könnte wenn write bei der Gruppe gesetzt ist die oben angeführten Aktionen durchführen.
* chmod 1XXX

## Set GID Bit (s)
* Wird auf Verzeichnisse gesetzt: Neu erstellte Dateien erhalten die Gruppe vom Verzeichnis
* Für Projektverzeichnisse sinnvoll
* chmod 2XXX

## Ausführbare Datein und Special Bits
Set UID Bit (s) ODER/UND Set GID Bit (s) => Auf einer ausführbaren Datei gesetzt: Der Prozess wird mit den effektiven Rechten des Eigentümers UND/ODER der Gruppe ausgeführt (z.B. /usr/bin/passwd)

## Prüfung von RPMs, ob jemand Änderungen durchgeführt hat
````
rpm -qf /usr/bin/ls #RPM herausfinden
rpm -V coreutils #RPM verifizieren
yum reinstall coreutils #Paket reinstallieren
````

## ACLs
* Ab RHEL7 werden ACLs vom Filesystem unterstützt
* ACLs werden bei der letzten Stelle der Berechtigungen mit + angezeigt
* ACLs werden nichtmitkopiert und gesichert
* Defaults bei Verzeichnissen (für Vererbung) mit `setfacl -m d:g:user:r-x /data`

## Commands
### umask
umask zieht die Berechtigungen ab die nicht gesetzt werden sollen
### cp
Berechtigungen sollen erhalten bleiben beim kopieren: `cp -p`
