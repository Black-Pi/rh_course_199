## File Permissions werden Sequentiell abgearbeitet
1. User Permissions
2. Group Permissions
3. Others

## Berechtigungen
````
sst rwx rwx rwx
421 421 421 421

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

## Commands
### umask
umask zieht die Berechtigungen ab die nicht gesetzt werden sollen
### cp
Berechtigungen sollen erhalten bleiben beim kopieren: `cp -p`
