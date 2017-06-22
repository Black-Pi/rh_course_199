
* atd = nur einmalige Jobs
* crond = wiederkehrende Jobs
* timer im systemd

## Verwendung at
````
[root@server2 ~]# at 13:41
at> echo "hallo philipp"
at> <EOT>
job 4 at Thu Jun 22 13:41:00 2017
# Ctrl+D aussteigen aus Prompt
````

## anacron
Prüft die Jobs die durch eine Nichtverfügbarkeit des Servers nicht gelaufen sind bzw. die Directories /etc/cron.*ly
/etc/con.hourly/0anacron
/etc/anacrontab

## Managing temporary files
````
systemd-tmpfiles-clean.{service,timer}
/usr/lib/tmpfiles.d
````
