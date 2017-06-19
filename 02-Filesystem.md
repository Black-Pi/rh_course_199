## Filesystem
* usr = unix system resources
* run = neues Hauptdirectory in RHEL7, Dateien die zur Laufzeit benötigt werden; ist ein tmpfs = Memory (fällt unter used im top)

## Man Pages sind in Sektionen eingeteilt
zu finden unter: man man

## tmp
* Dateien deren Access Zeitstempel sich 10 Tage nicht geändert hat, werden gelöscht (wird bis RHEL6 im anachron und cron.daily gesteuert)
* Ab RHEL7 ist es im /usr/lib/systemd/system/systemd-tmpfiles-clean.service bzw. systemd-tmpfiles-clean.timer
* Konfiguration unter /usr/lib/tmpfiles.d/tmp.conf

## Alias deaktivieren
\COMMAND

## inodes
* df -i => Anzahl inodes werden angezeigt (Erweiterungen bei xfs und ntfs möglich bei ext3 und ext4 nicht)
* Im inode werden Informationen wie welcher Typ (directory, link, pointer, block, character, file, usw.), Berechtigungen, Timestamps, uid, gid, link, Pointer zum Datenbereich, aber kein Dateiname
* Dateiname ist im Verzeichnis und hat den inode als Referenz
* Wenn eine Datei angegriffen wird wird immer von / weggegangen um die inodes aufzulösen (bei xfs hat .=128 und ..=128)
* => um eine Datei in einem Unterverzeichnis anzugreifen braucht man vom / weg zumindest bei others x-Berechtigungen

## Hard Link
* gleiche inode-Nummer (Referenz)
* Referenzzähler wird hochgezählt `-rw-r--r--.  2 root root 1921 Jun 19 13:26 philipp`
* inodes suchen: `find / -inum 1111111`
* Nachteil: nur auf reguläre Dateien; funktioniert nicht über Dateisystemgrenzen hinweg

## Commands
### stat
* relative access time: wird nur alle 24 Stunden aus Performancegründen geändert
* modify: inhalt hat sich geändert
* change: dateieigenschaft hat sich geändert

