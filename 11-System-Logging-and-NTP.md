* System Log Deamon: bei RedHat nur rsyslogd
* logger() => /dev/log <= journald (neu unter RHEL7) => DB unter /run/log/journald <= rsyslogd => /etc/rsyslog.conf => /var/log/...
* `grep '^[^#$]' /etc/rsyslog.conf` => `man 3 syslog` um facilitys und levels herauszufinden
* Nur debug Meldungen in ein File schreiben `*.=debug`
* Persitente Speicherung der Logdaten (nicht unter /run): einfach ein Dirctory /var/log/journal und richtige gruppe + gid bit setzen

## timedatectl
* Einstellung Datum/Zeit
* Zeitzone /etc/localtime

## Timeserver
mindestens 3

## journalctl
* alle optionen anzeigen: `journalctl -o verbose`
* z.B.: `journalctl _SYSTEM_UNIT=sshd.service _PID=1182`
* Beispiel alle Einträge seit 9h vom SSHD-Service: `journalctl --since 9:00:00 _SYSTEMD-UNIT="sshd.service"`
