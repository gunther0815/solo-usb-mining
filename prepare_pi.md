# Raspberry Pi vorbereiten

> Wenn der Raspberry Pi bereits eingerichtet ist, kann dieser Schritt übersprungen werden.

> SSH sollte aktiviert sein.

---

## Möglichkeit 1: Raspberry Pi OS [Original] verwenden

Der Raspberry Pi benötigt ein Betriebssystem (OS) welches auf eine Micro-SD Karte gesielt wird, die dann in den Raspberry Pi kommt. Beim Vorbereiten der SD-Karte können bereits einige praktische Grundeinstellungen für später vorgenommen werden.

1. [Raspberry Pi Imager herunterladen](https://www.raspberrypi.com/software/)

2. Micro-SD-Karte mit dem Computer verbinden

3. Raspberry Pi Imager starten

4. `OS wählen` -> `Raspberry Pi OS (other)` -> `Raspberry Pi OS Lite (32-bit)`

5. SD-Karte auswählen

6. Zahnrad (unten rechts) anklicken

    `Hostname` aktivieren und ausfüllen (unter dem Hostnamen taucht der Raspberry Pi später im Netzwerk auf, dies erspart das spätere Heraussuchen der IP-Adresse)

    `SSH aktivieren` 

    `Benutzername und Passwort setzen` (mit diesen Angaben kann sich später im System des Raspberry Pis eingeloggt werden)

    Wifi kann eingerichtet werden, die Verbindung via LAN ist aber eher zu empfehlen!

    `Speichern` drücken

    <!--![Imager](https://user-images.githubusercontent.com/108631209/177061261-761e8192-d44e-4b84-abd1-bf8082eaf8d2.png)-->
    <figure><img src="https://user-images.githubusercontent.com/108631209/177061261-761e8192-d44e-4b84-abd1-bf8082eaf8d2.png" alt="" width="400" /><!--<figcaption></figcaption>--></figure>

7. SD-Karte auswählen und „Schreiben“ drücken

8. Nachdem der Schreib Prozess abgeschlossen ist, kann die SD-Karte vom Computer getrennt und in den Raspberry Pi gesteckt werden

9. Nun die Strom- und Internetversorgung des Raspberry Pis anschließen und ca. 2 Minuten warten

---

## Möglichkeit 2: Raspiblitz verwenden

### Installieren von Raspiblitz auf einem Raspberry Pi (4GB oder 8GB empfohlen)

Die folgende Hardware und Software wurden verwendet:

* Raspberry Pi 4 4GB
* 1 TB Samsung T5 SSD
* Customized raspberry pi 4 aloy housing for better heat dissipation.
* Raspiblitz 1.8.0 ([https://github.com/rootzoll/raspiblitz](https://github.com/rootzoll/raspiblitz))

Für die Installation gibt es bereits eine ausführliche Anleitung auf Github ([https://github.com/rootzoll/raspiblitz](https://github.com/rootzoll/raspiblitz)). Im Falle von Problemen hilft hier auch die Raspiblitz Telegram Gruppe: [https://t.me/raspiblitz\_DE.](https://t.me/raspiblitz\_DE)

> :bulb: Das wars. Nun ist der Raspberry Pi bereit.

---

####  [Voraussetzungen](/requirements.md)  ᐊ  previous | next  ᐅ  [Mining Software installieren](/install_miner.md)
