## 1. Grundbegriffe

|Begriff|Erklärung|
|---|---|
|Netzwerk|Mehrere Geräte, die miteinander verbunden sind und Daten austauschen.|
|Client und Server|Der Client (z. B. Handy, Laptop) sendet eine Anfrage. Der Server (z. B. Webserver) antwortet und liefert die Daten.|
|LAN|Lokales Netz an einem Ort, z. B. zu Hause oder im Büro.|
|WLAN|Ein LAN per Funk (WiFi).|
|WAN|Großes Netz über Städte und Länder. Das Internet ist das größte WAN.|
|Privates Netz|Netz mit privaten IP-Adressen (z. B. `192.168.x.x`). Es gilt nur intern, nicht direkt im Internet.|
|Protokoll|Regelwerk, nach dem Geräte miteinander kommunizieren.|
|Netzwerkprotokoll|Regeln, wie Geräte im Netzwerk Daten senden, empfangen und verstehen (z. B. IP, TCP, HTTP).|
|Bit|Kleinste Informationseinheit im Computer: 0 oder 1. 8 Bit = 1 Byte.|

## 2. Netzwerkmodelle

### OSI-Modell (7 Schichten)

|Schicht|Name|Aufgabe|
|---|---|---|
|7|Anwendung|Programme, z. B. Browser, E-Mail|
|6|Darstellung|Format und Verschlüsselung der Daten|
|5|Sitzung|Verbindung starten, halten und beenden|
|4|Transport|Daten übertragen (TCP, UDP)|
|3|Vermittlung|Weg finden mit IP (Router)|
|2|Sicherung|Daten im lokalen Netz mit MAC liefern (Switch)|
|1|Bitübertragung|Kabel, Funk, Signale|

### TCP/IP-Modell (4 Schichten)

|Schicht|Name|Beispiele|
|---|---|---|
|4|Anwendung|HTTP, DNS, SMTP|
|3|Transport|TCP, UDP|
|2|Internet|IP|
|1|Netzzugang|Ethernet, WLAN, MAC|

### Wie Daten durch die Schichten wandern

- **Beim Senden:** Die Daten gehen von oben nach unten. Jede Schicht fügt Zusatzinformationen (Header) hinzu. Das heißt **Kapselung**.
- **Beim Empfangen:** Die Daten gehen von unten nach oben. Jede Schicht entfernt ihren Header wieder.

## 3. Adressen und Zahlen

|Begriff|Erklärung|
|---|---|
|IPv4-Adresse|Adresse eines Geräts im Netz. 32 Bit, vier Zahlen von 0 bis 255, z. B. `192.168.1.10`. Die Adressen werden knapp.|
|IPv6-Adresse|Neue Version der IP-Adresse. 128 Bit, Zahlen und Buchstaben, z. B. `2001:db8::1`. Praktisch unbegrenzt viele Adressen.|
|Öffentliche IP|Adresse, unter der dein Netz im Internet sichtbar ist. Sie wird vom Internetanbieter vergeben und gehört dem Router.|
|Private IP|Adresse im eigenen Netz, z. B. `192.168.1.10`. Sie gilt nur intern und wird vom Router (DHCP) vergeben.|
|Subnetzmaske|Zeigt, welcher Teil der IP das Netzwerk ist und welcher das Gerät, z. B. `255.255.255.0`.|
|Subnetting (CIDR)|Kurzschreibweise für die Subnetzmaske. Die Zahl nach dem Schrägstrich zeigt, wie viele Bits zum Netzwerk gehören. `/24` = `255.255.255.0` (254 nutzbare Geräte).|
|MAC-Adresse|Feste Hardware-Adresse der Netzwerkkarte. Sie gilt nur im lokalen Netz. Moderne Handys können eine zufällige MAC nutzen.|
|Port|Nummer, die zeigt, für welches Programm oder welchen Dienst die Daten sind (z. B. 80 = Web, 22 = SSH).|
|TTL|Time To Live. Zähler im Paket, jeder Router zieht 1 ab. Bei 0 wird das Paket gelöscht, so kreist es nicht ewig.|

## 4. Geräte und Kabel

|Begriff|Erklärung|
|---|---|
|Switch|Verbindet Geräte im LAN und leitet Daten nur an das richtige Gerät (per MAC).|
|Router|Verbindet verschiedene Netze, z. B. das Heimnetz mit dem Internet. Er wählt den Weg per IP.|
|Gateway|Der „Ausgang" aus dem lokalen Netz in ein anderes Netz, meist der Router (z. B. `192.168.1.1`).|
|Access Point|Stellt WLAN bereit und verbindet WLAN-Geräte mit dem Kabelnetz. Im Heimrouter ist er meist eingebaut.|
|Ethernet-Kabel|Normales Netzwerkkabel (RJ45, z. B. Cat6) für kabelgebundenes Netzwerk.|
|Patchkabel|Kurzes Ethernet-Kabel, das Geräte im Serverschrank verbindet (z. B. Switch und Patchpanel).|
|Konsolenkabel|Verbindet den Laptop direkt mit einem Router oder Switch für die Erstkonfiguration.|

## 5. Wichtige Dienste

|Begriff|Erklärung|
|---|---|
|DHCP|Gibt Geräten automatisch eine IP-Adresse (und Gateway, DNS).|
|DNS|Übersetzt Namen (`google.com`) in IP-Adressen.|
|NAT|Der Router übersetzt private IP-Adressen in eine öffentliche IP-Adresse.|
|ARP|Findet im lokalen Netz die MAC-Adresse zu einer bekannten IP-Adresse.|

## 6. Wegfindung und Test

**Wie weiß ein Paket sein Ziel und seinen Weg?**

- Das Paket trägt die **Ziel-IP** im Header.
- **DNS** liefert die IP zum Namen.
- Jeder **Router** schaut in seine Routingtabelle und gibt das Paket an den **nächsten Router** weiter.
- Die Ziel-IP bleibt gleich, die **MAC-Adresse** wechselt bei jedem Schritt.

|Begriff|Erklärung|
|---|---|
|Ping (ICMP)|Testet, ob ein Gerät erreichbar ist, und misst die Antwortzeit. ICMP ist das Protokoll für Test- und Fehlermeldungen. Beispiel: `ping 8.8.8.8`|
|Traceroute|Zeigt den Weg eines Pakets über alle Router bis zum Ziel. Es nutzt die TTL. Befehl: `traceroute google.com` (Windows: `tracert`).|

## 7. Protokolle

|Protokoll|Erklärung|
|---|---|
|TCP|Überträgt Daten zuverlässig und vollständig. Verlorene Pakete werden neu gesendet.|
|UDP|Schnell, aber ohne Garantie (z. B. Videoanruf, Spiele).|
|HTTP|Protokoll für Webseiten, unverschlüsselt (Port 80).|
|HTTPS|HTTP mit Verschlüsselung durch TLS (Port 443).|
|FTP|Überträgt Dateien, unverschlüsselt (Port 21).|
|SFTP|Überträgt Dateien sicher über SSH (Port 22).|
|SMTP|Sendet E-Mails (Port 25 oder 587).|
|SSH|Secure Shell. Sicherer, verschlüsselter Fernzugriff auf einen anderen Computer über die Kommandozeile (Port 22).|
|TLS|Verschlüsselt die Verbindung, damit niemand mitlesen kann.|

## 8. Netze aufteilen (VLAN)

**VLAN** (Virtual LAN) teilt ein physisches Netzwerk, z. B. einen Switch, in mehrere getrennte virtuelle Netze auf. Geräte in verschiedenen VLANs sehen sich nicht direkt.

|Vorteil|Erklärung|
|---|---|
|Sicherheit|Gäste-WLAN und Firmennetz sind getrennt.|
|Übersicht|Jede Abteilung hat ihr eigenes Netz.|
|Weniger Last|Weniger unnötiger Datenverkehr im Netz.|

**Beispiel in einer Firma:** VLAN 10 für Mitarbeiter, VLAN 20 für Gäste, VLAN 30 für Server. Verkehr zwischen den VLANs läuft über einen Router.

## 9. Sicherheit

|Begriff|Erklärung|
|---|---|
|Firewall|Filtert den Datenverkehr und schützt das Netzwerk vor unerwünschtem Zugriff.|
|VPN|Verschlüsselter Tunnel durch das Internet. Die öffentliche IP ändert sich, der Datenverkehr ist geschützt.|
|TLS|Verschlüsselung für sichere Verbindungen, z. B. bei HTTPS.|