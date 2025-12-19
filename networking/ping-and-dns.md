*************************************************************

Hinweis:

siehe dazu auch 'systemische_einordnung' im Repo "notes"

*************************************************************

# Ping und DNS – Nutzung zur systematischen Eingrenzung

Ich nutze `ping`, um Erreichbarkeitsprobleme gezielt
auf unterschiedliche Systemebenen zurückzuführen
und nicht pauschal als „Netzwerkproblem“ zu behandeln.
Entscheidend ist für mich dabei die Trennung
zwischen IP-basierter Erreichbarkeit
und namensbasierter Adressierung.

## IP-basierter Erreichbarkeitstest

Den Befehl `ping -c 10 8.8.8.8` setze ich ein,
um ausschließlich die Erreichbarkeit auf Netzwerkebene zu prüfen.
Die Option `-c` begrenzt die Anzahl der gesendeten Pakete;
der Test endet nach einer definierten Anzahl von Versuchen
und liefert damit vergleichbare und dokumentierbare Ergebnisse.

In den Test fließen die lokale Netzwerkschnittstelle,
die Routing-Entscheidungen entlang des Netzwerkpfads
sowie die Fähigkeit des Zielsystems ein,
ICMP-Pakete zu empfangen und zu beantworten.
Eine Namensauflösung findet nicht statt.

Ich nutze diesen Test gezielt,
um DNS als Fehlerquelle auszuschließen
und festzustellen, ob eine grundlegende
IP-basierte Verbindung besteht.
Scheitert der Test, verorte ich die Ursache
auf der Netzwerkebene.

## Namensbasierter Erreichbarkeitstest

Mit `ping -c 10 google.com` erweitere ich den IP-basierten Test
um die Namensauflösung.
Der Domainname wird vor dem ersten Paket
über DNS in eine IP-Adresse übersetzt;
erst danach beginnt der eigentliche Ping-Vorgang.

Die gemessenen Round-Trip-Zeiten
(min/avg/max/stddev) beziehen sich ausschließlich
auf die Paketlaufzeit
und enthalten keine DNS-Auflösung.
Ich verwende diesen Test daher nicht,
um die Dauer der Namensauflösung zu bewerten,
sondern um zu prüfen,
ob sie grundsätzlich funktioniert.

## Vergleich und Nutzung

Der diagnostische Nutzen ergibt sich für mich
aus dem Vergleich beider Tests.
Ist der IP-basierte Test erfolgreich,
während der namensbasierte Test fehlschlägt,
gehe ich von einer funktionierenden Netzwerkebene aus
und suche die Ursache auf einer zusätzlich
beteiligten Ebene,
insbesondere bei der Namensauflösung
oder in zielabhängigen Netzwerkpfaden.

Sind beide Tests erfolgreich,
betrachte ich die grundlegende Erreichbarkeit als gegeben
und verorte die Ursache eines Problems
oberhalb der Netzwerkebene,
beispielsweise bei Diensten oder Anwendungen.

Ich nutze `ping` damit nicht zur Leistungsbewertung,
sondern als Werkzeug zur reproduzierbaren,
systematischen Eingrenzung von Fehlerursachen.


