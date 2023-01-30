# Miner.php Datei

cgminer ab der Version 4.12.1 liefert eine PHP-Datei aus namens `miner.php` und ist im Verzeichnis der Miner-Software zu finden. Wenn man diese durch den u.U. bereits vorhandenen Apache-Webserver anzeigen lassen will, so hat man für das interne Netzwerk eine brauchbare Anzeige über den Browser.

Auf dem RaspiBlitz läuft bereits eine Version des Apache2, der man nur noch beibringen muss PHP-Dateien zu akzeptieren. Dazu gibt es mehrere Dutzend Anleitungen im Netz, in Kürze läuft das etwa so:

```console
sudo apt-get install -y libphp_XXX YYYY
```

Für die Darstellung der Datei `miner.php` im Browser muss man diese Datei zunächst in das Verzeichnis des Webservers kopieren (auf dem Raspi ist das `/var/www/html`) oder man legt einen sogenannten Softlink (oder symlink oder symbolic link) im Verzeichnis des Webservers an und veweist auf die genannte Datei nach diesem Schema `ln -s /path/to/file /path/to/symlink`:

```console
ln -s /home/admin/Mining/cgminer_4.12.1/miner.php /var/www/html/
```

Nun kann man überprüfen ob sich unter der Adresse des Webservers ein Datei `miner.php` befindet durch Aufrufen der Adresse `http://<HOSTNAME>/miner.php` im Browser, `<HOSTNAME>` muss eben durch die IP-Adresse Eures Raspis ersetzt werden. Das Ergebnis sieht dann so aus:

<img src=".assets/miner-php.JPG" alt="miner.php" width="100%" />

---

#### [⚙️ cgminer API scripts](/cgminer_JAVA_API_Scripts.md)  ᐊ  previous | next  ᐅ  [❄ Troubleshooting](/troubleshooting.md)
