# Mining Software installieren

> Strom und Internet des Raspberry Pis müssen verbunden sein.

> USB Miner verbinden bzw. USB Hub einschalten.

Um nun vom eigenen Computer auf den Raspberry Pi via SSH zugreifen zu können muss sich der Computer im selben Netzwerk befinden. Ist dies der Fall öffnet man das Terminal. Dazu einfach auf dem PC nach dem Programm „Terminal“ suchen. Im Terminal geht es dann los:

1. Via SSH auf den Raspberry Pi zugreifen

```shell
ssh solominer@miner.local
```

solominer ist dabei der Benutzername, miner ist der Hostname (alternativ IP-Adresse des Raspberry Pis als Hostname verwenden)
yes eingeben und ENTER drücken -> Passwort eingeben und ENTER drücken
(beim Eingeben des Passworts gibt das Terminal keine Rückmeldung)

2. Updates durchführen

```shell
sudo apt-get update 
sudo apt-get upgrade -y
```

3. Pakete installieren

```shell
sudo apt-get install -y build-essential git autoconf automake libtool pkg-config libcurl4-openssl-dev libudev-dev libusb-1.0-0-dev libncurses5-dev
```

4.	Jetzt kann der CGMiner Branch aus GIT geklont werden:

```shell
mkdir -p mining; cd mining 
git clone https://github.com/kanoi/cgminer.git
cd cgminer
```

5.	Nach erfolgreichem Klonen aus GIT kann der CGMiner nun kompiliert werden:

```shell
./autogen.sh
CFLAGS="-O2 -Wall -march=native -fcommon" ./configure --enable-gekko
sudo make
```

(An dieser Stelle den Raspberry Pi mit sudo reboot neustarten, falls der nächste Schritt nicht funktioniert)

6.	Nun kann der Fortschritt folgendermaßen getestet werden:

```shell
sudo ./cgminer -n
```

In der Antwort sollte dann die Bezeichnung des Miners auftauchen. Hier ein Beispiel:

```shell
…
Manufacteur: 'GekkoScience'
Product: 'NewPac Bitcoin Miner'
…
```

Nun ist alles installiert und das Mining kann beginnen!

---

#### [Raspberry Pi vorbereiten](/prepare_pi.md)  ᐊ  previous | next  ᐅ  [Mining Software starten](start_mining.md)
