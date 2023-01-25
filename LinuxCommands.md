# 💡 Tipps und Tricks für eine erleichterte Bedienung unter Linux/Raspberry Pi

Linux ist vor allem in der Kommandozeile stark. Um auch weniger versierten Bastlern ein paar hilfreiche Befehle mit an die Hand zu geben, die ihr Arbeitsleben unter Linux so komfortable wie möglich gestalten sollen, werde ich hier ein paar dieser Befehle auflisten.

⚠️ Diese Befehle müssen so wie sie gezeigt werden keinen großen Sinn ergeben, sondern dienen der Illustration der Machbarkeit.

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

Erläuterungen folgen in Kürze
- ssh-keygen --> private-key in `/home/<user>/.ssh/id_rsa` und public-key in `/home/user/.ssh/id_rsa.pub`
- Ändern der Rechte: `cd ~/.ssh` und `chmod 600 id_rsa`
- Übertragen des Keys auf den Raspi: `ssh-copy-id admin@raspberrypi.local`
- einloggen mit `ssh admin@raspberrypi.local`

---

#### [❄ Troubleshooting](/troubleshooting.md)  ᐊ  previous | next  ᐅ  [💡 PV/HomeAssistent/InfoTicker etc.](additional-links.md)
