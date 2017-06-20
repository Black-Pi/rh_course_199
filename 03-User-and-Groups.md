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

### Using Identity Management Services
* Kerberos: /etc/krb5.conf
* PAM: /etc/pam.d/password-auth
* authconfig, authconfig-tui, system-config-authentication
* pam Module für LDAP, Kerberos installieren
* SSSD Modul: kümmert sich um die Authentifizierung der User (egal von wo die User kommen)
** /etc/sssd/sssd.conf => Konfiguration der Repositories (LDAP, Kerberos, usw.)
* RedHat Doku für AD-Integration: https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html-single/Windows_Integration_Guide/index.html
