# 🌩 Übertakten

## Der Spaß-Teil

<!-- > :warning: **Warning:** Do not push the big red button.  -->

<!-- > :memo: **Note:** Sunrises are beautiful.  -->

<!-- > :bulb: **Tip:** Remember to appreciate the little things in life.  -->

> **ACHTUNG**: Übertakten sorgt für eine höhere Leistungsaufnahme. Es ist dringend anzuraten sich **vorher** über ein geeignetes Kühlkonzept Gedanken zu machen, da man Gefahr läuft den Chip **dauerhaft zu schädigen**. Ich rate niemandem zum Tunen des Systems, vor allem da der Mehrwert relativ gering ist.

Eine kleine Anregung für ausreichende Kühlung:

<table><tr><td><img src="../.assets/Kühlkörper.jpg" alt="Kühlkörper" width="400" /></td><td><img src="../.assets/IMG-1285.jpg" alt="Kühlkörper" width="400" /></td><td><img src="../.assets/IMG-1286.jpg" alt="Kühlkörper" width="400" /></td></tr></table>

Hierzu wurde ein CPU-Kühler mit Heatpipes anstatt des Standard-Kühlkörpers verbaut. Unbedingt Wärmeleitpaste verwenden für eine optimale Wärmeableitung.

Die Standard-Spannung liegt bei 1.45V. Aus der Beschreibung des **Gekkoscience Compaq F** USB-Miners lassen sich des Weiteren folgende Werte als Anhaltspunkt ablesen:

| Frequency (MHz)        | 400  | 500  | 545  | 600  | 700  | 800  |
| ---------------------- | ---- | ---- | ---- | ---- | ---- | ---- |
| USB Hub Power (Ampere) | 2.00 | 2.75 | 3.00 | 3.30 | 4.00 | 5.00 |
| Hash Speed (GH/s)      | 200  | 300  | 366  | 400  | 460  | 550  |

> **Anmerkung:** Je höher die Hashrate desto größer ist die Abweichung vom Durchschnitt, bedingt durch Herstellungstoleranzen des ASIC.

Spannung kann am Potentiometer eingestellt und wie folgt gemessen werden:
<figure>
    <img src="../.assets/Potentiometer.JPG" alt="Potentiometer" width="400" />
    <figcaption>Bild vom Potentiometer</figcaption>
</figure>
Die Einstellung am Potentiometer sollte umgehend mit einem Multimeter verifiziert werden. Da der Abgriff auf der Rückseite des zu kühlenden ASICs ist, kann die Überprüfung schon in Stress ausarten, da man ja eine höhere Spannung einstellt und somit zwangsläufig mehr Wärme abführen muss.

<figure>
    <img src="../.assets/Spannungsabgriff.JPG" alt="Spannungsabgriff" width="400" />
    <figcaption>Bild vom Spannungsabgriff</figcaption>
</figure>


Zum eigentlichen übertakten kann nun die Core-Spannung von standardmäßig 1.45V durch drehen am Potentiometer erhöht werde. Grundsätzlich sollte die Erhöhung in winzigen Schritten erfolgen mit anschließender Prüfung ob die Kühlung noch ausreicht und ob das Mining noch stabil läuft.

Die Stabilität kann einfach mittels **cgminer** und dem bereits genannten auto-tuning-Parameter geprüft werden. Gegebenenfalls senkt das auto-tuning die Frequenz automatisch ab.

Die Kühlung zu überprüfen ist hier schon eine größere Herausforderung. Dies kann idealerweise durch eine Wärmebildkamera überprüft werden:

<figure><img src="../.assets/IMG-1181.JPG" alt="Wärmeentwicklung" width="400" /><figcaption>Wärmeentwicklung mit Standard-USB-Hub: ca. 8W</figcaption></figure>
<figure><img src="../.assets/IMG-1183.JPG" alt="Wärmeentwicklung" width="400" /><figcaption>Wärmeentwicklung mit Standard-USB-Hub: ca. 8W</figcaption></figure>
