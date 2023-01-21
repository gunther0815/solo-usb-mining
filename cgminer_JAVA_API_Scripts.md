# cgminer JAVA API Skripte

Als Ergänzung zur bereits bestehenden Abstraktionebene der Java API, können weitere Shell- oder Pythonskripte dienen. Weitere Beispiele sollen folgen, gerne können hier auch nützliche Skripte aus der Community geteilt werden.

## Skript zum ändern der Frequenz

Wenn man aus welchen Gründen auch immer häufig die Frequenz seines USB-Miners ändert, bietet es sich an diesen Schritt zu vereinfachen, da (für mich) die Syntax zum Verändern der Frequenz schwer merkbar ist, ich den Befehl doppelt ausführen muss (für `target` und `frequenz`) und gegebenfalls vorher in der Bash-Historie nachsehen muss.

Das folgende Shellscrip soll genau dies tun.

Dafür muss ein Shellscript im Ordner der Wahl angelegt werden, z.B. in '/home/admin/Mining':

```console
sudo nano /home/admin/Mining/cgminer-api.sh
```

und folgender Inhalt geschrieben werden:

```bash
#!/bin/bash
cd /home/admin/Mining/cgminer_4.12.1/

device=$1
freq=$2
target=$3
java API "ascset|$device,target,$target"
java API "ascset|$device,freq,$freq"
```

Für die Ausführung müssen nun noch die Rechte des Skriptes angepasst werden, das geht mit dem Befehl `chmod`:

```console
sudo chmod 755 /home/admin/Mining/cgminer-api.sh
```

Nun kann das Skript mit Übergabeparametern gestartet werden (der Pfad kann ggf. weggelassen werden):

```console
/home/admin/Mining/cgminer-api.sh 0 450 470
```

> :memo: **Zur Erklärung:** Der Übergabeparameter `0` entspricht dem `$1` des Skripts und wird der Variablen `device` zugewiesen. Dieser Wert ist in der GUI des Miners zu prüfen bzw. kann er auch über die API abgefragt werden (z.B. mit `java API devs` wird die ID angezeigt `[ID] => 0`, und entspricht der zu verwendenden Nummer). Ebenso werden die Werte `450` und `470` nach dem gleichen Mechanismus den Variablen `freq` und `target` zugewiesen. Das Skript setzt diese Variablen dann lediglich bei den beiden aufeinander folgenden Java API-Aufrufen ein.

Die Ausführung wird mit der Rückgabe des Status quittiert:

```console
Attempting to send 'ascset|0,target,470' to 127.0.0.1:4028
Answer='STATUS=S,When=1674301921,Code=119,Msg=ASC 0 set OK,Description=cgminer 4.12.1|'
[STATUS] =>
(
   [STATUS] => S
   [When] => 1674301921
   [Code] => 119
   [Msg] => ASC 0 set OK
   [Description] => cgminer 4.12.1
)
Attempting to send 'ascset|0,freq,450' to 127.0.0.1:4028
Answer='STATUS=S,When=1674301922,Code=119,Msg=ASC 0 set OK,Description=cgminer 4.12.1|'
[STATUS] =>
(
   [STATUS] => S
   [When] => 1674301922
   [Code] => 119
   [Msg] => ASC 0 set OK
   [Description] => cgminer 4.12.1
)
```

---

#### [⚙️ cgminer JAVA API](/cgminer_JAVA_API.md)  ᐊ  previous | next  ᐅ  [❄ Troubleshooting](/troubleshooting.md)
