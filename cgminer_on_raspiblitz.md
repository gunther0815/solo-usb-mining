# cgminer auf RaspiBlitz installieren

Wir verbinden uns mit dem Raspiblitz und sehen das Menu oder den Download der Blockchain

![image](https://user-images.githubusercontent.com/108099690/203105607-45735953-d43f-427a-afec-fdea43d085ef.png)

Hier gehen wir nun mit ```STRG + C``` aus dem Menu und danach ins Verzeichnis, wo wir später den Mining Ordner haben möchten, in meinem Fall im „home“ Verzeichnis, der 
Befehl ```cd``` bringt euch in die Verzeichnisse, der Befehl ```ls``` bzw. ```ls -ls``` listet auf, was sich dort gerade befindet, wo ihr seid.
Aktuell befindet sich also kein CG Mining Ordner im Verzeichnis „home“

(Mit ```clear``` wird euer Bildschirm übrigens wieder ansehnlich)

![image](https://user-images.githubusercontent.com/108099690/203105156-0626b9aa-b59f-486e-b3a8-645c4a9f4a02.png)

Erst einmal installieren wir die benötigten Pakete, für die CGMiner Software, wie im Github beschrieben, mit:
```
sudo apt-get install -y build-essential git autoconf automake libtool pkg-config libcurl4-openssldev libudev-dev libusb-1.0-0-dev libncurses5-dev screen
```
„screen“ wurde nur hinzugefügt, da ich damit arbeite, aber da müsst ihr gucken, was euch am besten passt

Nun klonen wir die Mining Software, von Github, auf unseren Raspiblitz, mit:
```
sudo git clone https://github.com/kanoi/cgminer.git
```

![image](https://user-images.githubusercontent.com/108099690/203105854-38d40551-0ed4-4d53-beab-4014dfac00e8.png)

Nun befindet sich der „cgminer“ Ordner in unserem „home“ Verzeichnis:

![image](https://user-images.githubusercontent.com/108099690/203105995-909c31ad-4f4a-4562-b50b-0ef444a3e1e0.png)

Jetzt wird noch kompiliert mit:

```sudo CFLAGS="-O2 -march=native -fcommon" ./autogen.sh --enable-gekko --enable-icarus```
und danach
```sudo make```

Und wir sind bereit für den Betrieb des Miners vom Raspiblitz aus

---

#### [Raspberry Pi vorbereiten](/prepare_pi.md)  ᐊ  previous | next  ᐅ  [Mining Software starten](start_mining.md)
