# 💡 Tipps und Tricks für eine erleichterte Bedienung unter Linux/Raspberry Pi

Linux ist vor allem in der Kommandozeile stark. Um auch weniger versierten Bastlern ein paar hilfreiche Befehle mit an die Hand zu geben, die ihr Arbeitsleben unter Linux so komfortable wie möglich gestalten sollen, werde ich hier ein paar dieser Befehle auflisten.

⚠️ Diese Befehle müssen so wie sie gezeigt werden keinen großen Sinn ergeben, sondern dienen der Illustration der Machbarkeit.

⚠️ Unter Linux kann man Pfade `relativ` oder `absolut` angeben. Wenn man den Unterschied kennt, ist die Navigation durch die Pfade sehr viel einfacher und auch die Lesbarkeit von Beispielen erhöht sich massiv. Siehe hierzu z.B. https://www.selflinux.org/selflinux/html/verzeichnisse_unter_linux02.html

## `history`, `!`, `grep` und `tail`

`history` zeigt alle Befehle die bereits einmal eingegeben wurden, als Liste an:

```console
history | tail -n 10
  938  sudo screen -r miner
  939  cd Mining/cgminer_4.12.1/
  940  history | grep frequency
  941  history | grep frequ
  942  history | grep freq
  943  history | grep api
  944  java API "ascset|0,freq,400"
  945  sudo screen -r miner
  946  history
  947  history | tail -n 10
```

Wie man anhand der fortlaufenden Nummer sehen kann, kann diese Befehlshistorie sehr lang sein, weswegen ich sie mit `tail -n 10` auf die letzten 10 Einträge begrenzt habe. Das `|`-Zeichen (genannt "pipe") verknüpft hierzu die Befehle `history` und `tail`

Ebenso ist es möglich nach bestimmten Befehlen in der Befehlshistorie zu suchen. Ich suche nun nach einem Befehl der in meienr Erinnerung mit dem Skript `cgminer.sh` zu tun hatte. Wieder begrenze ich die Anzahl der gefundenen Einträge auf die letzten 10:

```console
history | grep cgminer.sh | tail -n 10
  844  sudo su - -c "screen -dm -S miner /home/admin/Mining/cgminer.sh"
  846  sudo su - -c "screen -dm -S miner /home/admin/Mining/cgminer.sh"
  848  sudo nano /home/admin/Mining/cgminer.sh
  849  sudo su - -c "screen -dm -S miner /home/admin/Mining/cgminer.sh"
  917  cat cgminer.sh
  921  sudo su - -c "screen -dm -S miner /home/admin/Mining/cgminer.sh"
  950  history | grep cgminer.sh
  951  history | grep cgminer.sh | tail -n 10
  952  cat /home/admin/Mining/cgminer.sh
  953  history | grep cgminer.sh | tail -n 10
```

Damit ich nun einen aufwendigen Befehl wie in Zeile 921 `sudo su - -c "screen -dm -S miner /home/admin/Mining/cgminer.sh"` nicht erneut eintippen muss, genügt es die Zeilennummer hinter ein Ausrufezeichen `!` zu setzen, und der entsprechende Befehl wird unmittelbar ausgeführt. Der Anschaulichkeit halber, weil der Befehl `cat` auch eine Rückgabe liefert, verwende ich `!952` als Demonstration:

```console
!952
cat /home/admin/Mining/cgminer.sh
#!/bin/bash
cd /home/admin/Mining/

sudo ./cgminer_4.12.1/cgminer --api-listen --api-allow "W:192.68.2.0/24,W:127.0.0.1" 2> "logs/run-`date +%Y%m%d%H%M%S`.log"
```

---

## SSH auth-key auf Raspberry Pi hinterlegen

Durch Abspeichern eines Authentication Keys des Host-PCs auf dem Raspberry Pi entfallen bei der SSH-Verbindung die Passworteingaben. Dies ist vor allem hilfreich wenn man über die API Mining-Daten auf dem Host-PC automatisiert anzeigen lassen will.

> ```diff 
> Erläuterungen folgen in Kürze
> - ssh-keygen --> private-key in `/home/<user>/.ssh/id_rsa` und public-key in `/home/user/.ssh/id_rsa.pub`
> - Ändern der Rechte: `cd ~/.ssh` und `chmod 600 id_rsa`
> - Übertragen des Keys auf den Raspi: `ssh-copy-id admin@raspberrypi.local`
> - einloggen mit `ssh admin@raspberrypi.local`
> ```

## crontab verwenden für zeitgesteuerte Leistungsanpassung (z.B. des R909)

> :warning: Für dieses Beispiel wird eine funktionierende Java API benötigt. Siehe dazu [⚙️ cgminer JAVA API](/cgminer_JAVA_API.md).

Mittels crontab können auf einem Raspberrypi oder anderem Linux-basiertem System abhängig von der Zeit Befehle ausgeführt werden. Als Beispiel dient hier der Versuch den R909 USB-Miner von Monatg 00:00 Uhr bis Freitag 23:59 Uhr mit einer Frequenz von 350MHz zu betreiben, am Wochenende von Samstag 00:00 Uhr bis Sonntag 23:59 Uhr jedoch mit 470 MHz. Ob dies ein realistisches Szenario ist, bleibt jedem selbst überlassen, als Anschauungsbeispiel ist es aber hervorragend geeignet.

Als erstes öffnen wir in der Konsole die Konfigurationsdatei in der alle cronjobs gespeichert sind. Dies geht ganz einfach so:

```console
crontab -e
```

beim ersten Aufruf kann hierzu einfach der Editor ausgesucht werden. Später wird crontab die Konfigurationsdatei immer mit diesem Editor verwenden. Wir verwenden für die zeitliche Steuerung das Skript aus Kapitel [⚙️ cgminer API scripts](/cgminer_JAVA_API_Scripts.md):

```console
# Starte Montag 00:00 Uhr mit 350MHz
00 00 * * MON /home/admin/Mininig/cgminer-API.sh 0 350 350

# Starte Samstag 00:00 Uhr mit 470MHZ
00 00 * * SAT /home/admin/Mininig/cgminer-API.sh 0 470 470
```

Wie gewohnt mit dem Editor Eurer Wahl speichern. Die angelegten Jobs können mir `crontab -l` ausgegeben werden, mit `crontab -r` können sie gelöscht werden. Es gibt nahezu keine Einschränkunegn der zeitlichen Steuerung, einfach mal ein bisschen im Internet recherchieren.

Von nun an wird der R909 zeitlich ferngesteuert. Zum Ausprobieren der Syntax in cron kann man die Zeiten in die nahe Zukunft legen und einfach live beobachten:

```console
# Starte Dienstag 14:30 Uhr mit 350MHz
30 14 * * TUE /home/admin/Mininig/cgminer-API.sh 0 350 350

# Starte Dienstag 14:35 Uhr mit 400MHz
35 14 * * TUE /home/admin/Mininig/cgminer-API.sh 0 400 400

# Starte Dienstag 14:40 Uhr mit 415MHz
40 14 * * TUE /home/admin/Mininig/cgminer-API.sh 0 415 415
```

---

#### [💡 Bildergalerie](Galerie.md)  ᐊ  previous | next  ᐅ  [💡 PV/HomeAssistent/InfoTicker etc.](additional-links.md)
