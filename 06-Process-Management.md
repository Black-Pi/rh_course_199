## Load Average
* Running and Blocked Prozesse in der Zeitspanne
* Best Case: #CPU = Load-Average
* Abfrage mit `vmstat 1`


## Commands
### kill -l
* Signale anzeigen
````
kill -2 (SIGINT) => beenden des Prozess
kill -3 (SIGQUIT) => Coredump erstellen
kill -15 (SIGTERM) => default
kill -19 (SIGSTOP) => Prozess stoppen, mit kill -18 (SIGCONT) wieder starten
kill -1 (SIGHUP) => Prozess soll Konfigurationsdateien neu einlesen
````

### top
* F-Taste: Sortierung umstellen
* Cursor-Taste rechts Sortierung ändern
* W Speichern der Einstellungen für diesen User
* r => reneice von Prozessen (-werte => besser, +werte => schlechter)

### time
real = Gesamtzeit incl. io
user = reine Rechenzeit
sys = System calls
