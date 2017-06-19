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

## Scripts bei RPMs anzeigen
* Fehler: "Scriptlet failed" `rpm -q --scripts PACKAGENAME`

## Commands
### usermod
Weitere Hilfsgruppe zu Susi hinzufügen: `usermod -a -G wheel susi`
