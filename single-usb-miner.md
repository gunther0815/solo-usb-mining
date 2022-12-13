# ☀ Single USB-Miner

## Ein erster Einstieg in USB-Mining.

Hier wird die Basis zum Mining geschaffen mit Fokus auf die Hardware.

Zur Ermittlung der Leistungsfähigkeit des USB-Miners in der jeweiligen Hardware-Konfiguration wird das Auto-tuning der cgminer-Software verwendet:

```shell
// sudo ./cgminer --compact --real-quiet -o stratum+tcp://solo.ckpool.org:3333 -u <BITCOINADDRESS>.<OPTIONAL_NAME> -p x --gekko-compacf-freq 500 --gekko-start-freq 200 --gekko-mine2 --gekko-tune2 60
```

Die Start- und Endfrequenz kann man jederzeit ändern, sobald man ein Gefühl dafür hat was die eigene Hardware leistet. Ein Standard-USB-Hub kann sich durchaus bei 280MHz einpendeln (Nicht genug Strom vergfügbar), bei geschickt gewählter Hardware sind auch deutlich höhere Taktraten möglich.

Der USB-Miner nimmt sich die Leistung die er benötigt für die eingestellte Taktrate. Durch das Auto-tuning können wir die Taktrate in MHz so lange erhöhen, bis sich der Algorithmus von cgminer auf eine stabile Taktrate einpendelt, hier sind das ca. 530MHz.

<figure><img src="broken-reference" alt=""><figcaption><p>Wird durch anderes Bild ersetzt.</p></figcaption></figure>

Die Leistungsfähigkeit bei z.B. 330MHz sind in meinem Fall 230GH/s (Gigahashes pro Sekunde), bei 530MHz schafft mein Miner satte 355GH/s.

Bei angestecktem USB-Tester sehen wir die angelegte Spannung (in Volt), den verwendeten Strom (in Ampere) und die daraus resultierende elektrische Leistung (in Watt):

<figure><img src="../.assets/IMG-1254.jpg" alt=""><figcaption><p>USB Safety Tester</p></figcaption></figure>

Aktive (mit Netzteil) Standard-USB-Hubs mit einem Gekkoscience Compaq F können hierbei extrem unterschiedlich sein. Ich habe Taktraten von 270MHz bis 545MHz gesehen, je nach verwendetem USB-Hub.

**ACHTUNG**: höhere Taktraten erfordern aktive Kühlung (siehe dazu auch Kapitel [uebertakten.md](uebertakten.md "mention")).
