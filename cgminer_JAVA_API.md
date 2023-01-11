# cgminer JAVA API

cgminer erlaubt das Abrufen von Statistiken und Parametern via API (`A`pplication `P`rogramming `I`nterface oder deutsch Anwendungsschnittstelle), z.B. Bestshare, die Anzahl gefundener Blöcke, aber auch das Setzen von Systemparametern während des Betriebes von außen, z.B. die Frequenz (MHz) oder den USB-waitfactor. Des Weiteren kann das Mining-Programm ferngesteuert werden. Aber eins nach dem anderen... 

## Installation der Java Runtime Environment (JRE)

Für die Benutzung der API muss die Java Laufzeitumgebung installiert werden. Wir beziehen uns hier auf eine Linux-Umgebung auf einem Raspberry Pi 4. 

Zuerst muss die passende Laufzeitumgebung für das System gesucht werden, das macht man mittels `apt` über den folgenden Befehl:

```bash
apt-cache search jre
```

Was zu folgendem Output in der Konsole führt:

```console
libanimal-sniffer-java - JDK/API verification tools
libcommons-exec-java - Java library to reliably execute external processes from within the JVM
docbook-xsl - stylesheets for processing DocBook XML to various output formats
libgeronimo-osgi-support-java - Java libraries providing OSGi lookup support for Geronimo projects
default-jre - Standard Java or Java compatible Runtime
default-jre-headless - Standard Java or Java compatible Runtime (headless)
jaxws - JAX-WS Reference Implementation (Command Line Tools)
libjaxws-java - JAX-WS Reference Implementation (Library)
libjaxws-api-java - Java API for XML-Based Web Services
libjreen-qt5-1 - powerful Jabber/XMPP library implemented in Qt5/C++
libjreen-qt5-dbg - powerful Jabber/XMPP library (Qt5 build) - debugging symbols
libjreen-qt5-dev - powerful Jabber/XMPP library (Qt5 build) - development files
libambix-utils - AMBIsonics eXchange library (utilities)
libhtmlcleaner-java - Java HTML Parser library
libhtmlcleaner-java-doc - Java HTML Parser library (documentation)
libjregex-java - regular expressions for Java
libreoffice - office productivity suite (metapackage)
libtwelvemonkeys-java - collection of plugins and extensions for Java\'s ImageIO
libtwelvemonkeys-java-doc - Documentation for libtwelvemonkeys-java
openjdk-11-jre - OpenJDK Java runtime, using Hotspot JIT
openjdk-11-jre-headless - OpenJDK Java runtime, using Hotspot JIT (headless)
openjdk-11-jre-zero - Alternative JVM for OpenJDK, using Zero
openjdk-17-jre - OpenJDK Java runtime, using Hotspot JIT
openjdk-17-jre-headless - OpenJDK Java runtime, using Hotspot JIT (headless)
openjdk-17-jre-zero - Alternative JVM for OpenJDK, using Zero
libopenjfx-java - JavaFX/OpenJFX - Rich client application platform for Java (Java libraries)
libsaaj-java - SOAP with Attachment API for Java
java-package - Utility for creating Java Debian packages
```

Nun haben wir die richtige Laufzeitumgebung ermittelt (`openjdk-11-jre-headless`) und installieren diese wiederum mittels `apt` (Ich habe während der Installtion `openjdk-11-jre-headless` verwendet, `openjdk-17-jre-headless` sollte auch ohne weiteres möglich sein.):

```shell
apt-get install openjdk-11-jre-headless
```

Nun sind wir bereit für die Konfiguration der Java API für cgminer. 

## Konfiguration

Um die API benutzen zu können müssen wir cgminer mitteilen, dass Anfragen von außen (entweder vom Raspberry Pi selbst via 'localhost' oder aus einem privaten Adressbereich zu Hause (subnet xxx.xxx.xxx.0/24) akzeptiert werden und die Software Informationen über den Miningprozess nach außen mitteilt). Die Konfiguration kann entweder beim Start von cgminer als Parameter mitgegeben werden:

```shell
sudo ./cgminer_4.12.1/cgminer --api-listen --api-allow "W:192.168.2.0/24,W:127.0.0.1"
```

In meinem Beispiel erlaube ich Anfragen vom Raspi selbst aus via localhost `127.0.0.1` und aus dem privaten Adressbereich meines Subnetzes `192.168.168.xxx`.

Diese Einstellung kann auch in der Konfigurationsdatei `cgminer.conf` gemacht werden:

```console
...
"api-description" : "cgminer 4.12.1",
"api-mcast-addr" : "224.0.0.75",
"api-mcast-code" : "FTW",
"api-mcast-des" : "",
"api-mcast-port" : "4028",
"api-port" : "4028",
"api-host" : "127.0.0.1",
...
```

## Beschreibung der API

Um API-Befehle ausführen zu können, muss man entweder den Pfad von cgminer mit angeben oder sich im Pfade des Programmes befinden. Dies verdeutliche ich beim ersten Befehl folgend.

### java API estats

```shell
~/Mining/cgminer_4.12.1/java API estats
```

ergibt folgenden Output:

```console
[STATUS] =>
(
   [STATUS] => S
   [When] => 1673472697
   [Code] => 70
   [Msg] => CGMiner stats
   [Description] => cgminer 4.12.1
)
[STATS0] =>
(
   [STATS] => 0
   [ID] => GSF0
   [Elapsed] => 2754
   [Calls] => 0
   [Wait] => 0.000000
   [Max] => 0.000000
   [Min] => 99999999.000000
   [Serial] => GS-10070001
   [Nonces] => 15126
   [Accepted] => 15102
   [TasksPerSec] => 292.136834
   [Tasks] => 803956
   [BusyWork] => 0
   [Midstates] => 4
   [MaxTaskWait] => 3363
   [WaitFactor0] => 0.300000
   [WaitFactor] => 1.200000
   [FreqBase] => 5.000000
   [FreqFail] => 0.000000
   [TicketDiff] => 64
   [TicketMask] => 0x000000fc
   [TicketNonces] => 15094
   [TicketBelow] => 0
   [TicketOK] => false
   [GHZeroDelta] => 0
   [GHLast] => 299
   [GHNonces] => 1667
   [GHDiff] => 106688
   [GHGHs] => 1529.411011
   [Require] => 0.650000
   [RequireGH] => 995.903963
   [JobDataAge] => 0.001268
   [Jobs] => 9837/17486/17515/17416/17467
   [JobElapsed] => 33.65/60.00/60.00/60.00/59.99
   [JobsPerSec] => 292.32/291.44/291.91/290.26/291.13
   [JobsAvgms] => 3.42/3.43/3.43/3.45/3.43
   [JobsMinMaxms] => 3.12:12.05/3.13:13.50/3.11:13.16/3.13:14.62/3.14:13.57
   [cur_off_0_0] => 0
   [cur_off_1_-4] => 0
   [cur_off_2_-8] => 0
   [cur_off_3_-12] => 0
   [Rolling] => 1529411.011201
   [Resets] => 0
   [Frequency] => 380.000000
   [FreqComp] => 379.999390
   [FreqReq] => 380.000000
   [FreqStart] => 380.000000
   [FreqSel] => 380.000000
   [Dups] => 12
   [DupsReset] => 12
   [Chips] => 6
   [FreqLocked] => false
   [USBProp] => 1000
   [Chip0Nonces] => 2714
   [Chip0Dups] => 1
   [Chip0Ranges] => 512/595/616/570/421/0/2714/83.15%
   [Chip0FreqSend] => 380.000000
   [Chip0FreqReply] => 380.000000
   [Chip1Nonces] => 2261
   [Chip1Dups] => 0
   [Chip1Ranges] => 429/476/503/492/361/0/2261/69.27%
   [Chip1FreqSend] => 380.000000
   [Chip1FreqReply] => 380.000000
   [Chip2Nonces] => 2808
   [Chip2Dups] => 2
   [Chip2Ranges] => 533/601/638/598/438/0/2808/86.03%
   [Chip2FreqSend] => 380.000000
   [Chip2FreqReply] => 380.000000
   [Chip3Nonces] => 2311
   [Chip3Dups] => 2
   [Chip3Ranges] => 440/508/507/496/360/0/2311/70.80%
   [Chip3FreqSend] => 380.000000
   [Chip3FreqReply] => 380.000000
   [Chip4Nonces] => 2713
   [Chip4Dups] => 1
   [Chip4Ranges] => 517/558/614/559/465/0/2713/83.11%
   [Chip4FreqSend] => 380.000000
   [Chip4FreqReply] => 380.000000
   [Chip5Nonces] => 2295
   [Chip5Dups] => 6
   [Chip5Ranges] => 443/499/488/520/345/0/2295/70.31%
   [Chip5FreqSend] => 380.000000
   [Chip5FreqReply] => 380.000000
   [NonceByte-00] => 130.128.123.131.114.6.3.0.0.1.62.133.119.123.130.65
   [NonceByte-10] => 4.1.2.1.0.125.148.129.122.108.4.1.0.0.0.55
   [NonceByte-20] => 118.141.101.141.65.2.1.3.0.0.117.129.118.124.125.5
   [NonceByte-30] => 1.2.1.0.59.126.129.142.114.58.2.2.2.2.0.0
   [NonceByte-40] => 113.128.126.139.120.4.1.1.0.0.52.150.140.121.122.58
   [NonceByte-50] => 0.1.1.0.1.116.126.131.142.131.1.2.2.0.0.66
   [NonceByte-60] => 149.133.135.118.58.1.0.1.2.1.135.102.119.119.129.3
   [NonceByte-70] => 1.0.0.0.65.136.155.124.107.59.1.0.0.0.0.0
   [NonceByte-80] => 118.117.118.113.117.5.1.0.0.0.56.128.107.114.120.68
   [NonceByte-90] => 3.0.0.0.0.118.117.129.118.119.7.3.1.0.0.70
   [NonceByte-A0] => 120.112.128.148.52.4.1.0.1.0.116.118.116.120.98.2
   [NonceByte-B0] => 0.0.0.2.75.130.126.122.143.56.2.0.0.1.0.0
   [NonceByte-C0] => 122.126.137.118.114.1.1.1.0.0.72.151.103.130.111.52
   [NonceByte-D0] => 3.0.0.0.0.146.134.134.127.115.3.0.0.1.0.62
   [NonceByte-E0] => 118.133.124.148.52.2.1.0.0.0.141.127.135.119.120.1
   [NonceByte-F0] => 5.0.1.0.65.149.126.116.121.48.2.1.1.0.0.0
   [nb2c-00] => 0.0.0.0.0.0.0.0.0.0.0.1.1.1.1.1
   [nb2c-10] => 1.1.1.1.1.2.2.2.2.2.2.2.2.2.2.2
   [nb2c-20] => 3.3.3.3.3.3.3.3.3.3.4.4.4.4.4.4
   [nb2c-30] => 4.4.4.4.4.5.5.5.5.5.5.5.5.5.5.5
   [nb2c-40] => 0.0.0.0.0.0.0.0.0.0.0.1.1.1.1.1
   [nb2c-50] => 1.1.1.1.1.2.2.2.2.2.2.2.2.2.2.2
   [nb2c-60] => 3.3.3.3.3.3.3.3.3.3.4.4.4.4.4.4
   [nb2c-70] => 4.4.4.4.4.5.5.5.5.5.5.5.5.5.5.5
   [nb2c-80] => 0.0.0.0.0.0.0.0.0.0.0.1.1.1.1.1
   [nb2c-90] => 1.1.1.1.1.2.2.2.2.2.2.2.2.2.2.2
   [nb2c-A0] => 3.3.3.3.3.3.3.3.3.3.4.4.4.4.4.4
   [nb2c-B0] => 4.4.4.4.4.5.5.5.5.5.5.5.5.5.5.5
   [nb2c-C0] => 0.0.0.0.0.0.0.0.0.0.0.1.1.1.1.1
   [nb2c-D0] => 1.1.1.1.1.2.2.2.2.2.2.2.2.2.2.2
   [nb2c-E0] => 3.3.3.3.3.3.3.3.3.3.4.4.4.4.4.4
   [nb2c-F0] => 4.4.4.4.4.5.5.5.5.5.5.5.5.5.5.5
   [NTimeout] => 57136
   [NTrigger] => 14234
   [SleepN] => 3614818
   [SleepAvgReq] => 1184.972371
   [SleepAvgRes] => 1.065132
   [SleepN1_1] => 384185
   [SleepAvgReq1_1] => 1040.603884
   [SleepAvgRes1_1] => 1.181619
   [SleepN1_5] => 67541
   [SleepAvgReq1_5] => 1045.310034
   [SleepAvgRes1_5] => 2.169598
   [SleepInv] => 1
   [WorkGenNum] => 803956
   [WorkGenAvg] => 14.122006
   [Over1N] => 9866
   [Over1Avg] => 1286.910805
   [Over2N] => 755690
   [Over2Avg] => 71.888137
   [SWCount] => 1480896
   [SWAvg] => 64.395541
   [SWMin] => 35
   [SWMax] => 14272
   [SW0Count] => 0
   [SW10Count] => 1480896
   [SW100Count] => 71812
   [USB Pipe] => 0
   [USB Delay] => r0 0.000000 w0 0.000000
   [USB tmo] => 1106145 0
)
```

### java API summary

```shell
java API summary
```

oder `java api` ohne Parameter ergibt folgenden Output:

```console
[STATUS] =>
(
   [STATUS] => S
   [When] => 1673473153
   [Code] => 11
   [Msg] => Summary
   [Description] => cgminer 4.12.1
)
[SUMMARY] =>
(
   [0] => SUMMARY
   [Elapsed] => 3211
   [MHS av] => 1509805.86
   [MHS 5s] => 2102945.36
   [MHS 1m] => 1602801.57
   [MHS 5m] => 1535146.52
   [MHS 15m] => 1480010.79
   [Found Blocks] => 0
   [Getworks] => 180
   [Accepted] => 2492
   [Rejected] => 0
   [Hardware Errors] => 896
   [Utility] => 46.56
   [Discarded] => 788340
   [Stale] => 0
   [Get Failures] => 0
   [Local Work] => 1725434
   [Remote Failures] => 0
   [Network Blocks] => 8
   [Total MH] => 4848011150.0000
   [Work Utility] => 21092.99
   [Difficulty Accepted] => 1123762.00000000
   [Difficulty Rejected] => 0.00000000
   [Difficulty Stale] => 0.00000000
   [Best Share] => 3152534
   [Device Hardware%] => 0.0793
   [Device Rejected%] => 0.0000
   [Pool Rejected%] => 0.0000
   [Pool Stale%] => 0.0000
   [Last getwork] => 1673473153
)
```

---

#### [⚙️ R909](R909.md)  ᐊ  previous | next  ᐅ  [❄ Troubleshooting](/troubleshooting.md)
