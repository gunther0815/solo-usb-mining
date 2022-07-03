# Voraussetzungen
Da der üblichste Weg fürs Solo-Mining ein Raspberry Pi ist, wird ab hier ausführlich beschrieben, wie man einen solchen einrichtet und damit das Mining später startet.

Um den Raspberry Pi einzurichten und alles Nötige zu installieren, muss auf das Gerät zugegriffen werden. Dafür gibt es zwei verschiedene gängige Methoden.
- Über das Netzwerk vom eigenen Computer aus (SSH)
- Am Raspberry Pi angeschlossenes Display, Tastatur und ggf. Maus
Die erste Methode ist die bequemere, da der Raspberry Pi nur an Strom und Internet angeschlossen sein muss. Dadurch kann er überall stehen, solange er im selben Netzwerk ist (möglichst über LAN), wie der Computer, von dem aus der Raspberry Pi bedient werden soll.
Die zweite Methode ist die zunächst intuitivere für alle die noch nie in der Kommandozeile (Terminal) auf einem Computer waren. Für die Einrichtung wird der Raspberry Pi dann an einem Display angeschlossen und die Eingaben werden mit einer direkt angeschlossenen Tastatur gemacht. Ein großer Nachteil ist, dass alle Befehle entweder manuell eingetippt werden oder auf den Raspberry gebracht werden müssen (als Datei oder über Internet).
Im Folgenden wird der Weg beschrieben um mit der ersten Methode, also Via SSH, den Raspberry Pi fürs Mining vorzubereiten und das Mining zu starten. Die ganze Einrichtung ist nur „Copy&Paste“, sodass auch jeder Anfänger sich an die Methode via SSH wagen sollte, bevor er direkt ein Display und eine Tastatur für den Raspberry Pi frei macht.
