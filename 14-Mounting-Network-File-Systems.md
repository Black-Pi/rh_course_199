## NAS vs. SAN
* Network Attached Storage vs. Storage Area Network
* NAS => CIFS (SMB) or NFS
* SAN => Fibre Channel, FCoE, iSCSI
* NAS => remote freigegebene Filesysteme
* SAN => Blockdevice (Disk)
* NFS: Network File System

## NFS
* rpc-bind, mountd, nfs services müssen bei der FW-Freigegeben werden
* `mount serverX:/directory/1/ /mnt`
* in fstab anstatt defaults: soft,bg,intr,sync (soft=beim starten des systems nach einer gewissen Zeit aufhören, bg=background)
* automount: `yum install autofs`

## NFS mit Kerberos
* keytab - Files auf beide Seiten (restorecon beim abholen des Tickets ausführen)
* nfs-secure auf beide Seiten aktivieren
* mount -o sec=krb5p servername:/shares /mnt

# CIFS Shares
* cifs-utils und samba-client Pakete
* smbmount -L ... => list der Freigaben
* in fstab die Option  credentials=... verwenden
