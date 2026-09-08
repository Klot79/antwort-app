# Antwort! v7 – Mac + AirPlay + iPhone Scanner

## Genau für den Unterricht gedacht

**MacBook:** Administrator + Lehrer-Spielmodus + AirPlay/Display  
**iPhone:** nur Scanner

### Ablauf

1. Auf dem Mac im Administratorbereich Fragen vorbereiten.
2. `Spielmodus` öffnen.
3. `Display` öffnen und dieses Fenster per AirPlay/Beamer zeigen.
4. Im Lehrer-Spielmodus wird ein 5-stelliger Raumcode angezeigt.
5. Auf dem iPhone `scan.html` öffnen und den Code eingeben.
6. Sobald der Lehrer **Start** drückt, startet der Scanner auf dem iPhone.
7. Jede erkannte Karte wird sofort an den Mac gesendet.
8. Auf dem Mac sieht der Lehrer unmittelbar:
   - 🟢/👍 richtig
   - ❗ falsch
   - Name des Schülers
   - gewählte Antwort
   - Anzahl gescannter Karten
9. Scannen läuft weiter, bis der Lehrer **Stop** drückt.
10. Stop zeigt die Gesamtergebnisse.
11. **Weiter** macht die nächste Frage bereit.
12. **Überspringen** beendet die laufende Frage und zeigt ebenfalls die Ergebnisse.

### Verbindung

Mac und iPhone verbinden sich direkt über PeerJS/WebRTC. Dadurch muss kein eigenes Backend eingerichtet werden. Beide Geräte brauchen Internet.

Die Karten bleiben unverändert: QR-Code enthält `ANTWORT:E01` bis `ANTWORT:E22`; die Antwort A/B/C/D wird aus der Drehung der Karte erkannt.

### Wichtig

Der iPhone-Scanner benötigt eine HTTPS-Adresse. GitHub Pages ist dafür geeignet.

Das Display ist absichtlich ohne Scan- und Lehrerbuttons, damit beim AirPlay nur die Frage, Antworten, Scan-Zahl und Ergebnisse zu sehen sind. Der Lehrer steuert ausschließlich auf dem Mac.
