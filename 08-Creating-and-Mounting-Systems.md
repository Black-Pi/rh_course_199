## MBR vs. GPT
* MBR alt (1980er Jahren)
* MBR: BIOS or (U)EFI with legacy Mode fürs booten
* MBR: fdisk, sfdisk, cfdisk, parted
* GPT wird zwingend bei Platten > 2TB benötigt
* GPT: (U)EFI firmware fürs booten
* GPT: gdisk, parted
* Test ob GPT oder MBR Partition: gdisk aufrufen => Info wird am Anfang angezeigt
* Filesysteme: 
** btrfs => new RHEL7, under technical preview, hat eine Form von Raid / LVMs eingebaut
** (ext2,ext3),ext4 => Performanceoptimierungen bei ext4 um 6% gegenüber ext3; keine Konvertierung von ext3 auf ext4 möglich; ext3/ext4 sind JournalFilesysteme (Metadatenbereich, in der eine Aktion vorab notiert wird und bei Vollendigung "abgehakt/commitet"), ext4 bis 12TB, offline Verkleinerung möglich, Vergrößerung mölich
** xfs (default) => new RHEL7, gibts bereits seit 90er Jahren, support bis 16ExiByte (man units), keine Verkleinerung möglich, Vergößerung möglich

## fstab
* async: Cache beim Lesen und Schreiben von der Platte; Kernel Parameter: alle 30 Sekunden bzw. wenn 10% dirtiy blocks im Cache werden die Daten geschrieben
* nouser: nur root darf mounten und umounten
* auto: auto-mount
* suid: special files/directories
* exec: exekutierbare Files können angelegt werden
* dev: devices können angelegt werden
* Filesystem-UUID (`blkid`) bzw. Label (muss mit `e2label` bzw. `xfs_admin -L /dev/sdb1` gesetzt werden) anstatt des Partitionsnamen vergeben, da beim Booten die Reihenfolge /dev/sda1 /dev/sda2 usw. verändert werden kann

## Disk einbinden
1. gdisk /dev/vdb
2. partprobe => funktioniert bei RHEL7 nur wenn eine neue Partition hinzugefügt wurde, löschen benötigt einen reboot
3. mkfs.xfs /dev/vdb1
4. Eintrag in /etc/fstab
5. Mount-Directory erstellen: /data
6. mount /data

## Swap Space
* Größe ist abhängig von der Applikation
* Ansonsten gilt die Regel: 0,5 Memory bis max. 16GB
