## firewalld
* /usr/lib/firewall.d/services/*.xml
* Definition der Port-Freischaltungen und Kernel-Module in xml-Files
* Eigene Regeln unter /etc/firewall.d/services/
* firewall-cmd --add-service=httpd --permanent
* `firewall-cmd --runtime-to-permanent` => neu seit RHEL7.3
* firewall-cmd --list-all [--permanent]
