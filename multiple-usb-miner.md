# ☀ Multiple USB-Miner

Mehrere Miner an einem USB-Hub zu betreiben überfordert ALLE Hubs die ich ausprobiert habe, außer der unten genannten Spezialhardware von Gekkoscience. Dies liegt vermutlich daran dass USB meist gar nicht für Ströme größer 1A spezifiziert ist und sich alle Hubs somit gemäß der Norm verhalten. Das hilft uns natürlich nicht weiter bei einem Stromhungrigen Gerät wie dem Gekkoscience Compac F.

Standard	| Spannung	| max. Stromstärke	| max. Leistung
---------------------------------------------------------
USB 1.0/1.1	| 5 V	| 0,1 A	| 0,5 W
USB 2.0	| 5 V	| 0,5 A	| 2,5 W
USB 3.0/3.1 (Gen1)	| 5 V	| 0,9 A	| 4,5 W
USB 3.1 (Gen2)	| 5 V	| 3 A	| 15 W
USB-BC 	| 5 V	| 1,5 A	| 7,5 W
USB-PD	| 5 V, 12 V, 20 V	| 5 A	| 100 W

Mit einem Standard-Hub konte ich zwar auch 2 USB-Miner betreiben, jedoch bei mageren 270 MHz (bzw. 150GH/s (ich erinnere mich nicht genau)).

Von daher die dringende Empfehlung zu einem ähnlichen Setup für mehrere USB-Miner:
* Gekkoscience USB-Hub
* Externe ATX-Netzteil (ich verwende ein BeQuiet Straightpower mit 480W)
* USB3-Verlängerungen (auch hier haben nur die USB3-Verlängerungen funktioniert, die eine USB2-Verlängerung die ich verwendete, konnte den Miner nicht in Betrieb nehmen. Der Grund hierfür ist mir unklar.) 

Der Gekkoscience USB-Hub benötigt ein externes Netzteil, welches im Original gekauft werden kann, der Hub bietet aber auch einen Anschluß für einen PCIe-6-Stecker wie er bei jedem ATX-Netzteil vorkommt.

<img src=".assets/GekkoHub.jpg" alt="Gekkoscience USB-Hub" width="400" />

Das Netzteil funktioniert nur wenn der Mainborad-Connector überbrückt wird, sonst läuft das Netzteil nicht an.

<img src=".assets/ATXNetzteil.jpg" alt="ATX Netzteil" width="400" />

Dazu reicht es in meinme Fall Pin 16 (PS_ON) und 18 (Masse) zu überbrücken:

<img src=".assets/ATXStecker.jpg" alt="Stecker des ATX-Netzteils" width="400" />

Standard-Pin-Belegung eines 24poligen ATX-Steckers:

<img src=".assets/ATXPinBelegung.png" alt="ATX Pinbelegung" width="200" />

---

Alternativ zur Brücke oben kann man auch einen Schalter für den 20- bzw. 24-poligen Anschluss bestellen:

<img src=".assets/ATX Schalter.png" alt="ATX Schalter" width="400" />

---

#### [⛏ Miner Einstellungen MHz/ mV](miner-settings.md)  ᐊ  previous | next  ᐅ  [🌩 Übertakten](/uebertakten.md)
