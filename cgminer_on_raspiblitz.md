# cgminer auf Raspberry Pi/RaspiBlitz installieren

Wir verbinden uns mit dem Raspiblitz und sehen das Menu oder den Statusbildschirm (Download- bzw. Syncstatus) der Blockchain.

<!--![image](https://user-images.githubusercontent.com/108099690/203105607-45735953-d43f-427a-afec-fdea43d085ef.png)-->
<figure>
    <img src="https://user-images.githubusercontent.com/108099690/203105607-45735953-d43f-427a-afec-fdea43d085ef.png" alt="" width="400" />
    <!--<figcaption></figcaption>-->
</figure>

Hier gehen wir nun mit `STRG + C` aus dem Menu und danach ins Verzeichnis, wo wir später den Mining Ordner haben möchten, in meinem Fall im „home“ Verzeichnis, der 
Befehl `cd` bringt euch in die Verzeichnisse, der Befehl `ls` bzw. `ls -ls` listet auf, was sich dort gerade befindet, wo ihr seid.
Aktuell befindet sich also kein CG Mining Ordner im Verzeichnis `home`.

(Mit `clear` wird euer Bildschirm übrigens wieder ansehnlich).

<!--![image](https://user-images.githubusercontent.com/108099690/203105156-0626b9aa-b59f-486e-b3a8-645c4a9f4a02.png)-->
<figure>
    <img src="https://user-images.githubusercontent.com/108099690/203105156-0626b9aa-b59f-486e-b3a8-645c4a9f4a02.png" alt="" width="400" />
    <!--<figcaption></figcaption>-->
</figure>

Erst einmal installieren wir die benötigten Pakete, für die CGMiner Software, wie im Github beschrieben, mit:

```shell
sudo apt-get install -y build-essential git autoconf automake libtool pkg-config libcurl4-openssl-dev libudev-dev libusb-1.0-0-dev libncurses5-dev screen
```

`screen` wurde nur hinzugefügt, da ich damit arbeite, aber da müsst ihr gucken, was euch am besten passt.

Nun klonen wir die Mining Software, von Github, auf unseren Raspiblitz, mit:

```shell
sudo git clone https://github.com/kanoi/cgminer.git
```

<!--![image](https://user-images.githubusercontent.com/108099690/203105854-38d40551-0ed4-4d53-beab-4014dfac00e8.png)-->
<figure>
    <img src="https://user-images.githubusercontent.com/108099690/203105854-38d40551-0ed4-4d53-beab-4014dfac00e8.png" alt="" width="400" />
    <!--<figcaption></figcaption>-->
</figure>

Nun befindet sich der `cgminer` Ordner in unserem `home` Verzeichnis:

<!--![image](https://user-images.githubusercontent.com/108099690/203105995-909c31ad-4f4a-4562-b50b-0ef444a3e1e0.png)-->
<figure>
    <img src="https://user-images.githubusercontent.com/108099690/203105995-909c31ad-4f4a-4562-b50b-0ef444a3e1e0.png" alt="" width="400" />
    <!--<figcaption></figcaption>-->
</figure>

Alternativ bietet es sich an einen Sammelordner für mehrere Versionen von cgminer anzulegen, z.B. `/home/admin/Mining`, wenn man z.B. die Versionen 4.12.0 und 4.12.1 im Wechsel betreiben möchte. Dazu müsste ein Ordner `Mining` angelegt werden und nach einem Wechsel in dieses Unterverzeichnis mittels `cd /home/admin/Mining` dort den obigen `git clone....`-Befehl auzuführen:

```shell
mkdir -p /home/admin/Mining
```

```shell
cd /home/admin/Mining
```

```shell
sudo git clone https://github.com/kanoi/cgminer.git
```
Falls mehrere Versionen installiert werden sollen, empfiehlt es sich den Ordner cgminer umzubenennen in z.B. `/home/admin/Mining/cgminer_4.12.1`. Dies kann man mit `mv /home/admin/Mining/cgminer /home/admin/Mining/cgminer_4.12.1`erledigen (ggf. `sudo` voranstellen falls höhere Rechte benötigt werden.

Nun wechseln wir in das Verzeichnis um die Konfiguration und Kompilierung zu starten:

```shell
cd /home/admin/Mining/cgminer
```

```shell
sudo CFLAGS="-O2 -march=native -fcommon" ./autogen.sh --enable-gekko --enable-icarus
```

und danach:

```shell 
sudo make
```

Und wir sind bereit für den Betrieb des Miners vom Raspiblitz aus.

---

Des Öfteren scheint es unter Linux Probleme mit dem `sudo make` zu geben. Der Kompiliervorgang bricht ab mit dem Hinweis dass auf eine fehlende Bibliothek verlinkt wird.

```shell
/usr/bin/ld: cannot find -lz: No such file or directory
```

Hier hilft es herauszufinden welche Bibliothek fehlt, diese nachzuinstallieren und den obigen Vorgang zu wiederholen. In unserem Fall fehlt `zliblg-dev`.

```shell
sudo apt install zliblg-dev
```

Und schon schliesst der Kompiliervorgang ohne Fehler ab.

---

#### [Raspberry Pi vorbereiten](/prepare_pi.md)  ᐊ  previous | next  ᐅ  [Mining Software starten](start_mining.md)
