* Ab RHEL7 ist die höchste uid 1000

# SSH
ssh Privat + Public Keys liegen unter /etc/ssh/ssh_host_ecdsa_key.pub; Prüfung direkt auf der Zielmaschine mit ssh-keygen -l -f ssh_host_rsa_key.pub => Fingerprint wird angezeigt
Prüfung am lokalen Host über Public Key; Prüfung am Remote-Host über /etc/passwd /etc/shadow
Passwortloser Login mit eigenem Schlüsselpaar: ssh-keygen ... 
Kopieren des Schlüssels auf Zielmaschine ssh-copy-id SERVERNAME
Bei der Verbindung wird nun nur mehr das Passwort des Private-Keys abgefragt
ssh-agent kann für das Caching der Passwörter verwendet werden (Parameter setzen) und anschließend ssh-add ausführen

### sshd_config
  PermitRootLogin no
  # AllowGroups wheel
  PasswordAuthentication no
  KerberosAuthentication yes
  PubkeyAuthentication yes

### redhat-support-tool


# Commands
### w
  wer ist gerade aktiv
  tty2 ... Virtuelle Console 2 (CTRL + ALT + F2)
### sysprep
  löschen ser SSH-Keys
### tar xvJf
  für .xz Files (bzip2)
