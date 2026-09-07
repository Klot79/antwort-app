# Antwort! —App

Eine lokale, moderne Antwortt-App Web-App.

## Start
1. `index.html` in einem Browser öffnen.
2. Für die Kamera ist in der Regel `https://` oder `http://localhost` nötig.
3. Unter **Schüler** Schüler anlegen.
4. Unter **Karten** die persönlichen Karten erzeugen und drucken.
5. Frage erstellen → richtige Antwort markieren → **Frage starten**.
6. Karten vor die Kamera halten.

## Kartenprinzip
Jede Karte enthält einen eindeutigen QR-Code für den Schüler. Die vier Drehungen entsprechen:
- ↑ A
- → B
- ↓ C
- ← D

Die App liest die QR-Code-Geometrie aus und bestimmt daraus die Orientierung.

## Daten
Schüler, Fragen und Ergebnisverlauf werden zunächst nur im `localStorage` des Browsers gespeichert. Es gibt keinen Server.

## Technische Hinweise
- QR-Scanning: jsQR
- QR-Erzeugung: QRCode.js
- Kamera: Browser `getUserMedia`
- Die Kamera-Funktion benötigt eine sichere Umgebung (HTTPS oder localhost).

Für eine echte Mehrgeräte-Klassenlösung sollte als nächster Schritt ein Backend mit Lehrer-Login, Klassen, Synchronisation und Cloud-Speicherung ergänzt werden.


## Version 2 – spielerische Schüleransicht
- 22 feste Emoji-Spieler
- Schüleransicht ohne Lehrer-Login
- Persönliche Statistik
- Auflösung nach jeder Runde
- Schüler sehen nicht die Antworten anderer
- Die gedruckten Antwortkarten bleiben persönliche Karten

### Datenschutz / Sichtschutz
Die App zeigt in der Schüleransicht bewusst keine Antwortverteilung und keine Antworten anderer Spieler. Für echte Klassenräume sollten die Karten außerdem so gestaltet/ausgedruckt werden, dass ein Schüler die Markierung eines Nachbarn nicht bequem ablesen kann.

### iPhone
Der Live-Scanner kann auf einem iPhone im Browser über die Kamera laufen. Für Kamerazugriff muss die Seite über HTTPS oder localhost bereitgestellt werden.


## Version 3 – Sichtschutz-Karten
Die Antwortkarten wurden auf einen visuellen Sichtschutz umgestellt:
- keine sichtbaren A/B/C/D-Beschriftungen
- neutrale Muster und Orientierungspunkte
- persönlicher QR-Code ist für Menschen praktisch nicht lesbar (sehr geringe Druck-/Anzeige-Opazität)
- die Kamera verwendet die QR-Geometrie zur Bestimmung der Orientierung
- im Scanner kann ein Sichtschutz aktiviert werden; Antwortbuchstaben werden dann im Lehrerfenster zunächst verborgen
- nach jeder Frage kann der Lehrer die richtige Antwort und die Gesamtverteilung sehen
- Schüler sehen weiterhin nur ihre persönliche Statistik

Wichtig: Für einen wirklich professionellen Scanner sollten die Marker später auf ArUco/AprilTag-ähnliche, orientierungsfeste Marker umgestellt werden. QR-Codes sind für die Identifikation geeignet, aber ihre Orientierungsbestimmung ist bei schlechten Winkeln/Verdeckungen weniger robust.


## Version 4 – Orientierungsmarker
Die Karten verwenden jetzt einen separaten, neutralen Orientierungsmarker. Die Antwort wird nicht mehr aus der QR-Code-Ausrichtung abgeleitet:
- QR-Code = nur Schüleridentität
- großer Marker = Antwortorientierung
- keine A/B/C/D-Beschriftung auf der Karte
- vier Seitenmarker für A/B/C/D
- browserbasierte Bildauswertung
- Sichtschutz bleibt aktiv
- auf iPhone/iPad nutzbar

Hinweis: Das ist eine browserbasierte Näherung. Für eine kommerzielle/hochzuverlässige Erkennung von 22 gleichzeitig hochgehaltenen Karten wäre eine native Computer-Vision-Implementierung mit echten ArUco/AprilTag-Markern und Perspektivkorrektur die nächste technische Ausbaustufe.


## Version 7 – Karten/Emoji-Fix
- 🪪 Karten-Seite ist garantiert in der Navigation vorhanden.
- 🖨️ Karten werden beim Öffnen der Seite automatisch für alle 22 Spieler erzeugt.
- 👥 Jeder Spieler hat sichtbar einen Emoji.
- 🦊 Die 22 Emoji-Identitäten bleiben stabil.
- ➕ „Schüler hinzufügen“ benennt einen der 22 vorhandenen Emoji-Spieler statt weitere IDs zu erzeugen.
- QRCode.js wird geprüft; bei fehlender Bibliothek erscheint eine klare Fehlermeldung.
