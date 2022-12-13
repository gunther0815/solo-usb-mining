# ⛏ Konfigurationstipps

Diese Seite beschreibt mögliche Konfigurationen von CGMIner auf einem Raspbery Pi

## CGMiner in debug mode 

Um möglichst detaillierte Informationen vor allem beim erstmaligen Setup zu bekommen, bietet es sich an CGMiner wie folgt zu starten:

```shell
// sudo ./cgminer -o stratum+tcp://solo.ckpool.org:3333 -u <BITCOINADDRESS>.<OPTIONAL_NAME> -p x --gekko-compacf-freq 500 --gekko-start-freq 200 --gekko-mine2 --gekko-tune2 60
```

In diesem Modus kann man übersichtlich die Leistung der angeschlossenen Miner beobachten, das Hotplugging-Verhalten untersuchen aber auch einfach nur Einstellungen on-the-fly vornehmen.

## CGMiner in silent mode

Der Betrieb im Hintergrund ist notwendig, wenn man nicht permanent eine remote Verbindung via SSH offen halten kann oder will, z.B. beim Betrieb von CGMiner auf einem Raspberry Pi. Der cgminer-Dienst kann einfach mit **nohup** im Hintergrund gestartet werden:

```shell
// nohup sudo ./cgminer --compact --real-quiet -o stratum+tcp://solo.ckpool.org:3333 -u <BITCOINADDRESS>.<OPTIONAL_NAME> -p x --gekko-compacf-freq 500 --gekko-start-freq 200 --gekko-mine2 --gekko-tune2 60 &
```

Man beachte hier die Optionen **--compact** und **--real-quiet**. Diese Optionen verringern das zu loggende Datenvolumen auf ein Minimum.

Man beachte hierbei das abschliessende &. Der Prozess läuft nun im Hintergrund und leitet seine Ausgabe in die Datei /home/admin/nohup.out um. Diese kann mit cat in der Konsole ausgegeben werden:

```shell
// cat /home/admin/nohup.out
```

Um den Prozess zu beenden, muss die Prozess-ID mittels **kill** terminiert werden. Dazu sucht man zuwerst die Prozess-ID:

```shell
// ps aux | grep cgminer
```

Dies zeigt entsprechende Prozess-IDs von CGMiner an und können wie folgt beendet werden:

```shell
// sudo kill <PROZESSID>
```

## cgminer mit mehreren Pools betreiben

Es bietet sich an auf mehreren Hochzeiten zu tanzen, um z.B. 70% der Zeit in einen Pool zu minen (Solo-Pool-Mining), 30% aber auf eigene Faust zu minen (echtes Solomining). Dies hat den Vorteil, dass man im Falle eines Blockfundes des Pools seinen Beitrag bekommt, also entweder den Anteil der geleisteten Shares wenn jemand anderes einen Block findet ODER die vereinbarte Blockbelohnung des Solo-Mining-Pools wenn man den Block selbst findet, gleichzeitig aber auch sein Glück ausreizt um ganz alleine einen Block zu finden. Das muss jeder für sich selbst herausfinden, die Anleitung dazu gibt es trotzdem hier.

Anpassen der Konfigurationsdatei **/root/.cgminer/cgminer.conf** um die Pools und Quotas bekannt zu geben:

```shell
// sudo nano -w /root/.cgminer/cgminer.conf
```

Eintragen der Pools ähnlich meinem Beispiel:

```shell
{
"pools" : [
        {
                "quota" : "70;stratum+tcp://solo.ckpool.org:3333",
                "user" : "<BITCOINADDRESS>.<OPTIONAL_NAME>",
                "pass" : "x"
        },
        {
                "quota" : "30;stratum+tcp://solo.ckpool.org:3333",
                "user" : "<BITCOINADDRESS>.<OPTIONAL_NAME>",
                "pass" : "x"
        }
]
,
...
"load-balance" : true
...
}
```

Wichtig hierbei die quotas (in meinem Beispiel 70% und 30%), aber auch die Option **load-balance** auf **true** zu setzen.
