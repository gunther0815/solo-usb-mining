# Inhalt

## Allgemeines

* 💡 Warum USB-Mining
* 💡 Was ist Lottery-Mining?

## Vorbereitung

* [☀ Einkaufsliste](shopping-list.md)
* [☀ Voraussetzungen](requirements.md)

## Installation

* [☀ Raspberry Pi vorbereiten](prepare_pi.md) bzw. [Installation von cgminer auf dem RaspiBlitz](cgminer_on_raspiblitz.md)
* [☀ Mining Software installieren](install_miner.md)

## Konfiguration

* [⛏ Mining Software starten](start_mining.md)
* [⛏ Mining Software - GUI Konfiguration](cgminer_GUIConfiguration.md)
* [⛏ Mining Software - Erweiterte Konfiguration](EnhancedConfiguration.md)
* [⛏ Miner Einstellungen MHz/ mV](miner-settings.md)
* [⛏⛏ Mehrere Miner betreiben](multiple-usb-miner.md)
* [🌩 Übertakten](/uebertakten.md): Hier widmen wir uns dem Tuning.
* [⚙️ R909](/R909.md): Hier widmen wir uns dem dem Gekkoscience Terminus R909.
* [⚙️ cgminer JAVA API](/cgminer_JAVA_API.md): Details zur Java API für cgminer.
* [⚙️ cgminer API scripts](/cgminer_JAVA_API_Scripts.md): Python-Skriptbeispiele um API effizienter auszulesen bzw. um die Konfiguration zu automatiseren
* [⚙️ miner-php](/miner-php.md): Mining-Feedback im Browser.
* [❄ Troubleshooting](/troubleshooting.md) zeigt die Probleme denen ich begegnet bin.

## Weitere Links

* [💡 Bildergalerie](/Galerie.md): "When Plebs Go Wild"
* [💡 Hilfreiche Kommandos für erleichterte Bedienung unter Linux/Raspberry Pi](LinuxCommands.md)
* [💡 PV/HomeAssistent/InfoTicker etc.](additional-links.md)
* 💡 Autoren & [Solo-USB-Mining Telegram Gruppe](https://t.me/BTC_solo_mining)

---

## Warum Solo-USB-Mining?

Beim USB-Mining macht das „Drumherum“ eher Spaß als der Gewinn. Die `6,25 BTC + transaction fees` sind aber immer noch eine tolle Sache. Denkt dran, ab etwa Mai 2024 sind es nur noch `3,125 BTC + transaction fees`.

Das Ganze sollte als ein Projekt gesehen werden, um Details des Minings zu ergründen und zu verstehen. Zudem stärkt es das Netzwerk und kommt einer Dezentralisierung des Minings zugute.

Das Schöne beim USB-Mining ist die niedrige Einstiegshürde, es ist also mit relativ wenig Kosten verbunden und es gibt viel zu Lernen. :)

Außerdem verbraucht der kleine USB-Miner wenig Strom, macht wenig Lärm und er nimmt wenig Platz weg.

---

## Was ist Lottery-Mining?

Beim Bitcoin Mining hat grundsätzlich jeder die Möglichkeit einen Block zu finden. Da die Industrie um das Mining weltweit sehr groß geworden ist und es bei jedem Block purer Zufall ist wer diesen findet, ist es üblich in einem Pool mit vielen anderen zusammen zu minen. Dort wird die Blockbelohnung dann bei einem gefundenen Block auf alle Poolteilnehmer aufgeteilt (anteilig je nach Hashrate).

Die Gewinnwahrscheinlichkeit kann auf dieser Seite berechnet werden: https://solochance.com/

Da es ohne einen Mining-Pool für eine Einzelperson extrem unwahrscheinlich ist einen Block zu finden, wird das Solo-Mining auch als Lottery-Mining bezeichnet. Man spielt sozusagen alle 10 Minuten Lotto indem man versucht den richtigen Hash für den nächsten Block zu raten.

Damit die Einrichtung für das Solo-Mining unkompliziert wird und die Schnittstelle zu den anderen Minern im Bitcoin Netzwerk gewährleistet ist, greift man normalerweise auf den sogenannten [solo-ckpool](https://solo.ckpool.org/) zurück. Dies ist kein üblicher Mining-Pool (wie oben beschrieben), sondern ein speziell eingerichteter Pool für Solo-Miner. Dabei bekommt derjenige der den Block findet die Belohnung alleine und gibt lediglich 2% an den „solo-ckpool“ ab (solange man keinen Block findet geht keinerlei Bezahlung an den Poolbetreiber).

Für das Lottery-Mining bieten sich USB-Miner aufgrund des geringen Stromverbrauchs besonders an. Das ganze Projekt kann aber auch mit leistungsstärkeren Minern umgesetzt werden, um die Gewinnwahrscheinlichkeit zu erhöhen. Dies lohnt sich aber nur wenn man den dafür benötigten Strom gratis oder sehr günstig bekommen kann.

---

## Value 4 value

Du kannst hier für das Projekt spenden und dafür sorgen, dass es weiterhin dokumentiert und ausgebaut wird:

<table border=1>
<tr><td>nearfear18@walletofsatoshi.com</td><td>lumpycarp37@walletofsatoshi.com</td></tr>
<tr><td><img width="150" alt="qr" src="https://user-images.githubusercontent.com/108099690/197496656-55d2d453-34d4-475a-83c0-1c1aa55bb963.png" /></td><td><img src=".assets/V4V.png" alt="Donate" width="150" /></td></tr>
<tr><td>Gunther0815</td><td>OneOfThePlebs</td></tr>
<!--<tr><td></td><td></td></tr>-->
</table>

---

####    [Inhalt](/README.md)  ᐊ  previous | next  ᐅ  [Einkaufsliste](/shopping-list.md)
