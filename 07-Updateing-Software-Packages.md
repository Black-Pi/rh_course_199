## Versionen von Paketen "locken"
yum-plugin-versionlock

## Alle verfügbaren Versionen eines Paketes anzeigen
yum list PACKAGENAME --showduplicates

## Bevorstehende Updates prüfen
yum updateinfo list

## yum history
````
yum history info NUMBER
yum history undo NUMBER_TO_RESET
````
## GPG Key
rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release

## GPG Keys abfragen
rpm -qa | grep gpg-pubkey

## EPEL Repository
* Ist für RedHat erlaubt
* https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
* epel-release-latest-7.noarch.rpm installieren => EPEL Repo wird angelegt


