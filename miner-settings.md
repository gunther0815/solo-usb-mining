Achtung: Alle Angaben sind ohne Gewähr und sollten daher mit Vorsicht genossen werden. 
Vieles wurde von dem [Bitcointalk Thread](https://bitcointalk.org/index.php?topic=5053833.0) entnommen.

Möchte man den Gekkoscience Newpac übertakten, ersetzt man `<arg>` von diesem Befehl:

`--gekko-newpac-freq <arg>`: Set GekkoScience 2Pac BM1384 frequency in MHz

durch eine beliebig andere Zahl (Ganzzahl in MHz).

Dies gilt auch für alle anderen Modelle:

`--gekko-2pac-freq <arg>`: Set GekkoScience 2Pac BM1384 frequency in MHz, range 6.25-500 (default 100.0)

`--gekko-compac-freq <arg>`: Set GekkoScience Compac BM1384 frequency in MHz, range 6.25-500 (default 150.0)

`--gekko-terminus-freq <arg>`: Set GekkoScience Terminus BM1384 frequency in MHz, range 6.25-500 (default 150.0)

> :warning: Eine höhere Frtequenz bedeutet eine höhere Leistungsaufnahme, dadurch steigt die Temperatur des Mining-Chips u.U. erheblich.

> :warning: Stellt man die Frequenz höher als `100`, so sollte man einen Lüfter anbringen (Siehe dazu auch die Kapitel [Einkaufsliste](shopping-list.md) und [🌩 Übertakten](/uebertakten.md)).

<!-- Dieser Teil gehört vermutlich in das Tuning-Kapitel und scheint sich ausschliesslich auf den Newpac zu beziehen??!!-->
Die Hashrate steigt dabei linear mit dem Takt: Doppelter Takt -> doppelte Hashrate.
Jeder Chip ist jedoch individuell. So hat der eine oder andere aus dem Forum den Miner auf 500 oder sogar 600 Mhz bringen können. Andere schaffen jedoch nur 450 Mhz oder weniger mit der Standardspannung.

Wird zu viel Takt eingestellt, kommt entweder eine Fehlermeldung "missing nonce" oder die Hashrate fällt ab. Dann muss der Takt wieder verringert werden. Man sollte sehr vorsichtig sein, insbesondere bei der Einstellung der Spannung, denn es können irreparable Schäden auftreten. Die Standardspannung scheint 830 mV zu sein. Laut Forum kann man den Miner auf bis zu 860 mV einstellen.

> :memo: Anmerkung: Im Antminer S9 ist der gleiche Chip wie im Newpac verbaut. Dort läuft er mit 900 mV und etwa 600 Mhz. Dieser wird jedoch die Temperatur überwacht und im Notfall abgeschaltet.
Es gibt noch die Möglichkeit mit Autotune den Miner selbst den maximalen Takt auszuprobieren. Dazu tastet er sich selbst langsam hoch. 

Im Forum wird erklärt, wie es geht:
> https://manualzz.com/doc/52944452/gekkoscience-newpac-usb-flash-drive-user-manual
Dort kann man sehen, wie die Spannung verändert werden kann.

---

#### [⛏ Mining Software - Erweiterte Konfiguration](EnhancedConfiguration.md)  ᐊ  previous | next  ᐅ  [⛏⛏ Mehrere Miner betreiben](multiple-usb-miner.md)
