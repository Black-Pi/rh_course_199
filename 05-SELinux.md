* Unix Permissons => DAC => Discretionary Access Control
* SELINUX => MAC => Mandatary Access Control
* SELinux dient dazu um Prozesse voneinander geschützt werden

## SELinux Security Label
* user:roles:type_t:sensivity_or_category
* Die 4. Stelle kommt von RedHat (type_t) und ist relevant
* type_t verknüpft die Allow Rules

## SELinux Änderungen
`chcon -t TYPE FILE/DIRECTORY` => hier kann es passieren, dass bei einem relabeling die Labes wieder verloren gehen
Verzeichnis + alles was im Verzeichnis liegt in die Policy eintragen: `semanage fcontext -a -t public_content_rw_t 'var/ftp/upload(/.*)?'`
Typs anzeigen: `semanage fcontext -l | grep '/var/ftp'`
Änderungen auf dem System nachvollziehen: /etc/selinux/targeted/contexts/files/file_contexts.local
Reparieren, so wie es sein sollte mit `restorecon -vR /var/ftp`

## Hilfestellungen
* grep sealert /var/log/messages
* In Konfigurationsfiles z.B. /etc/vsftpd/vsftpd.conf
* Paket: selinux-policy-devel, man Pages für Services man <servicename>_selinux ; Dokus aus RPM anzeigen: `rpm -qd selinux-policy-devel | grep ftpd*`

## Commands
### sestatus
### setenforce
0..ausgeschaltet, 1..eingeschaltet
### seinfo
kommt aus dem Paket setools-console
### sesearch
````
[root@server2 ~]# ps -eZ | grep syslog
system_u:system_r:syslogd_t:s0    375 ?        00:00:00 systemd-journal
system_u:system_r:syslogd_t:s0    476 ?        00:00:00 rsyslogd
[root@server2 ~]# ls -Z /var/log/messages 
-rw-------. root root system_u:object_r:var_log_t:s0   /var/log/messages
[root@server2 ~]# sesearch -A -s syslogd_t -t var_log_t -c file
Found 3 semantic av rules:
   allow syslogd_t logfile : file { ioctl read write create getattr setattr lock append unlink link rename open } ; 
   allow syslogd_t var_log_t : file { ioctl read write create getattr setattr lock append unlink link rename open } ; 
   allow daemon logfile : file { ioctl getattr lock append } ; 
### => syslog Prozess hat read, write, create Rechte

[root@server2 ~]# ls -Z /etc/rsyslog.conf 
-rw-r--r--. root root system_u:object_r:syslog_conf_t:s0 /etc/rsyslog.conf
[root@server2 ~]# sesearch -A -s syslogd_t -t syslog_conf_t -c file                                                                                                                                                
Found 1 semantic av rules:
   allow syslogd_t syslog_conf_t : file { ioctl read getattr lock open } ; 

### => nur Leserechte
[root@server2 ~]# ls -Z /etc/shadow
----------. root root system_u:object_r:shadow_t:s0    /etc/shadow
[root@server2 ~]# sesearch -A -s syslogd_t -t shadow_t -c file

### => keine Rechte

````
-s (source) -t (target) -c (type)
