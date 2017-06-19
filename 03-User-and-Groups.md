## uid
* root => UID 0
* UID 0 => System Administrator => root
* UID 1-999 => Serviceuser
* UID > 1000 => Loginuser-Accounts

## /etc/passwd
* chsh (Shell ändern eines Users) Mögliche Shells unter /etc/shells
* chfn (Finger Information: INFO)

## /etc/shadow
* !! account ist gesperrt
* Passwort redhat für susi setzen: `echo redhat | passwd --stdin susi`
* chage susi (Ablaufdatum, Passwortänderung, usw. setzen)
* chage -d0 susi (Passwort muss sofort geändert werden)

## /etc/gshadow
* Gruppenpasswörterverwaltung
* gpasswd wheel
* Gruppe Switchen für einen User der in mehrere Gruppen drinnen ist: `sg wheel` anschließend Passwort eingeben (eigene Shell wird gestartet)

## Defaults für User
* /etc/deflaut/useradd
** /etc/skel => alles was hier drinnen ist, bekommt der User in sein home-Directory rein
* /etc/login.defs

## user locken
* usermod -L -s /usr/sbin/nologin susi
* besser las userdel, damit Files die dieser User angelegt hat nicht einem neuen User vererbt werden, der neu angelegt wird (weil die nächste freie uid verwendet wird)

## Scripts bei RPMs anzeigen
* Fehler: "Scriptlet failed" `rpm -q --scripts PACKAGENAME`

## Commands
### usermod
Weitere Hilfsgruppe zu Susi hinzufügen: `usermod -a -G wheel susi`

### klist
Auflisten der Kerberos Tickets
