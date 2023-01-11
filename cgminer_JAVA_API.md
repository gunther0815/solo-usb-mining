# cgminer JAVA API

cgminer erlaubt das Abrufen von Statistiken und Parametern via API (`A`pplication `P`rogramming `I`nterface oder deutsch Anwendungsschnittstelle), z.B. Bestshare, die Anzahl gefundener Blöcke, aber auch das Setzen von Systemparametern während des Betriebes von außen, z.B. die Frequenz (MHz) oder den USB-waitfactor. Des Weiteren kann das Mining-Programm ferngesteuert werden. Aber eins nach dem anderen... 

## Installation der Java Runtime Environment (JRE)

Für die Benutzung der API muss die Java Laufzeitumgebung installiert werden. Wir beziehen uns hier auf eine Linux-Umgebung auf einem Raspberry Pi 4. 

Zuerst muss die passende Laufzeitumgebung für das System gesucht werden, das macht man mittels `apt` über den folgenden Befehl:

```shell
apt-cache search jre
```

Was zu folgendem Output in der Konsole führt:

```shell
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

```shell
...
"api-description" : "cgminer 4.12.1",                                                                                17 "api-mcast-addr" : "224.0.0.75",                                                                                     18 "api-mcast-code" : "FTW",                                                                                            19 "api-mcast-des" : "",                                                                                                20 "api-mcast-port" : "4028",                                                                                           21 "api-port" : "4028",                                                                                                 22 "api-host" : "127.0.0.1",
...
```

## Beschreibung der API

... folgt in Kürze ...

---

#### [⚙️ R909](R909.md)  ᐊ  previous | next  ᐅ  [❄ Troubleshooting](/troubleshooting.md)
