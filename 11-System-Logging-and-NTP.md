* System Log Deamon: bei RedHat nur rsyslogd
* logger() => /dev/log <= journald (neu unter RHEL7) => DB unter /run/log/journald <= rsyslogd => /etc/rsyslog.conf => /var/log/...
* `grep '^[^#$]' /etc/rsyslog.conf` => `man 3 syslog` um facilitys und levels herauszufinden
* Nur debug Meldungen in ein File schreiben `*.=debug`
