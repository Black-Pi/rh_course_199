* LVM unterstützt auch RAID 0,1,5,6
* in der fstab den /dev/mapper Namen eintragen (nicht wie bei den Partitionen die UUID), da dieser nie geändert wird
* nur bei ext4 (bei xfs irrelevant): letzte Stelle in der fstab bedeutet, ob das Filesystem geprüft werden soll. Bei / - Partition 1 bei allen anderen ext4 Partitionen 2
* `pvmove /dev/sda1 /dev/sdb` => Disk sda1 auf sdb kopieren
## LV Disk verkleinern
`lvreduce -L 200M -r /dev/vg_data/lv_disk1`

