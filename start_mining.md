# Mining Software starten

> :memo: **WICHTIG:** Man muss sich in dem Ordner vom cgminer befinden damit der Befehl zum Start funktioniert. Befindet man sich nicht im Ordner, weil z.B. der Raspberry Pi neugestartet wurde, gelangt man mit folgendem Befehl in den Ordner:

```shell
cd mining/cgminer
```

Um den cgminer und damit das Mining zu starten, muss folgender Befehl ausgeführt werden:

für NewPac:

```shell
sudo ./cgminer --compact --real-quiet -o stratum+tcp://solo.ckpool.org:3333 -u <BTCADRESSE> -p x --suggest-diff 32 --gekko-newpac-freq 100 --gekko-newpac-boost
```

für CompacF:

```shell
sudo ./cgminer --compact --real-quiet -o stratum+tcp://solo.ckpool.org:3333 -u <BTCADRESSE> -p x --gekko-compacf-freq 500 --gekko-start-freq 450 --gekko-mine2 --gekko-tune2 60
```

> `<BTCADRESSE>` muss mit der eigenen Bitcoin Adresse ausgetauscht werden

> Die Zahl hinter `--gekko-newpac-freq` bzw. `--gekko-compacf-freq` kann erhöht werden, um den USB-Miner mit einer höheren Taktrate laufen zu lassen (dadurch erhöht sich die Hashrate aber gleichzeitig auch die Temperatur, die der Miner erreicht)

Die Befehle `compact` und `real-quiet` solltet ihr am Anfang weglassen um zu sehen ob der Miner gut läuft. Ihr seht im Falle des Compac F-Miners z.B. auf welcher Frequenz er sich einpendelt. Je nach USB-Hub werden verschiedene Frequenzen nicht erreichet. 

> :warning: **Nochmal der Hinweis**: Compac F nie ohne Kühlung betreiben!

Kurzer Auszug der Erklärung der Befehle:

```
Allgemein:

  --compact                   Use compact display without per device statistics
  
  --real-quiet                Disable all output

Newpac:

  --suggest-diff <arg>        Suggest miner difficulty for pool to user (default: none)
 
  --compac-freq <arg>         Set GekkoScience Compac frequency in MHz, range 100-500 (default: 150.0)
  
  --gekko-newpac-boost

Compac F:

  --gekko-compacf-freq <arg>  Set GekkoScience CompacF BM1397 frequency in MHz, range 100-800 (default 200.0)
  
  --gekko-start-freq <arg>    Ramp start frequency MHz 25-500
  
  --gekko-mine2
  
  --gekko-tune2 60
```

> :warning: **Achtung:** Wenn das Terminal geschlossen wird, wird auch der Mining Prozess beendet!
> Damit das Mining im Hintergrund weiter läuft, kann man `nohup` oder `screen` verwenden, mehr Inormationen dazu im Kapitel [⛏ Mining Software - Erweiterte Konfiguration](EnhancedConfiguration.md).

<!--
```shell
nohup <COMMAND> &
```

Um zu überprüfen, ob der Mining Prozess läuft, kann folgender Befehl ausgeführt werden:

```shell
cat nohup.out
```

Es wird ein Standbild von dem Prozess gezeigt.
Der USB-Miner blinkt mit einer weißen LED, wenn das Mining aktiv ist. Dadurch kann unkompliziert und visuell überprüft werden, ob das Mining läuft.

Die aktiven Prozesse des Raspberry Pis können mit diesem Befehl angezeigt werden:

```shell
top
```

Um die Prozess Übersicht zu beenden einfach die `Q`-Taste drücken.

Damit der cgminer beendet werden kann muss folgender Befehl ausgeführt werden:

```shell
sudo kill 1234
```

Anstelle von `1234` muss die Prozess-Nummer vom cgminer eingefügt werden (Diese steht links in der Prozess Übersicht).

Wenn man den Befehl für den cgminer im Hintergrund mehrmals gestartet hat, läuft der cgminer mehrfach im Hintergrund. Es ist dann zu empfehlen die Prozesse zu beenden damit nur einer aktiv ist.
-->
---

## Statistiken abrufen:

https://solo.ckpool.org/
Seite aufrufen und unter `Statistics` seine BTC Adresse eingeben, die im Befehl verwendet wurde. Dort sind dann alle relevanten Daten hinterlegt.

> :bulb: **Fertig!** Prost und Glückauf beim Block finden! 👷

---

## Mehrere USB Miner einzeln ansteuern:

Wenn mehrere Gekko Miner gleichzeitig betrieben werden, diese aber unterschiedlich angesteuert werden sollen dann kann dies folgendermaßen gemacht werden:

`Bus Nummer` und `Device Nummer` herausfinden

```shell
lsusb
```

Es werden alle verbundenen Geräte aufgelistet. Der Gekko Newpac erscheint z.B. als „Future Technology Devices International, Ltd Bridge(I2C/SPI/UART/FIFO)“

Durch den Zusatz `--usb BusNummer:DeviceNummer` wird ein einzelner USB Miner angesprochen:

```shell
sudo ./cgminer --compact --real-quiet -o stratum+tcp://pool.ckpool.org:3333 -u <BTCADRESSE> -p x --suggest-diff 32 --usb 1:7 --gekko-newpac-freq 100
```

Dabei müssen die zuvor gefundenen `Bus-` und `Device Nummern` eingetragen werden (Im obigen Beispiel wäre die gefundene Bus Nummer `001` und die Device Nummer `007`, daher dann `--usb 1:7`)

Möchte man die Miner verschieden ansteuern, dann sollte man zunächst durch Ausprobieren ermitteln welcher Miner welcher Device Nummer zugeordnet ist. Dazu einfach den cgminer wie in Schritt 2 beschrieben für ein bestimmtes Gerät starten und beobachten welcher Mining Stick anfängt zu blinken.

---

####  [Mining Software installieren](/install_miner.md)  ᐊ  previous | next  ᐅ  [Mining Software - Erweiterte Konfiguration](EnhancedConfiguration.md)
