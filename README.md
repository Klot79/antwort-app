# Antwort! – v9

## Lehrer-Ablauf
1. `index.html` auf dem MacBook öffnen.
2. Schülernamen unter „Schüler“ eintragen.
3. Fragen manuell erstellen oder unter „PDF / Bild → Fragen“ Material einlesen.
4. Automatisch erzeugte Fragen im Bereich „Erzeugte Fragen prüfen“ bearbeiten und erst mit „Fragen übernehmen“ in die Fragenliste übernehmen.
5. „🎮 Unterricht starten“ drücken.
6. Das AirPlay-Display über „🖥️ Display“ öffnen und auf TV/Beamer spiegeln.
7. Auf dem iPhone `scan.html` öffnen und den fünfstelligen Raumcode vom MacBook eingeben.
8. „Frage starten“ drücken. Das iPhone startet den Kamerascan.
9. Kinder zeigen ihre persönliche Antwortkarte. Der Lehrer sieht sofort Name, Antwort und 👍/❗.
10. „Scannen stoppen“ → Ergebnis → „Weiter“. Nicht alle 22 Karten müssen gescannt werden.

## Technischer Aufbau
- Statisches GitHub-Pages-Projekt, kein Lehrer-Login.
- Gemeinsamer Zustand auf dem MacBook über `localStorage`.
- iPhone ↔ MacBook über PeerJS.
- Kamera-QR-Erkennung über jsQR.
- PDF-Text über PDF.js; Bilder und gescannte PDFs über Tesseract.js.
- Die Display-Seite enthält keine Kamera und keinen Lehrerbereich.
- Der Display-QR-Code wurde entfernt. Das iPhone verbindet sich über den sichtbaren fünfstelligen Raumcode.

Hinweis: Die automatische Fragenerzeugung ist eine lokale, regelbasierte Textanalyse. Für wirklich semantisch hochwertige KI-Fragen wäre ein sicherer serverseitiger KI-Dienst erforderlich.


## iPhone-Scanner
Im Administrator gibt es jetzt einen sichtbaren Button **„📱 Karten scannen öffnen“**. Er öffnet `scan.html` direkt. Auf dem iPhone wird dort der fünfstellige Raumcode des Lehrer-Spielmodus eingegeben. Nach der Verbindung startet beim Beginn einer Frage automatisch die Kamera.


## v11.1 – iPhone-Scanner erreichbar
Der Button „📱 Karten scannen“ öffnet den Scanner nun direkt per Seitenwechsel statt per neuem Fenster. Das ist auf iPhones/Safari zuverlässiger. Im Scanner gibt es ein eigenes Raumcode-Feld mit automatischer Großschreibung und Fokus.


## Ablauf nach dem Scan
Mit „Frage starten“ zeigt das Display sofort Frage und Antworten und das verbundene iPhone startet den Scanner. Jeder erkannte Scan zeigt auf dem iPhone kurz 👍 bei richtiger bzw. ❗ bei falscher Antwort. Nach „Scannen stoppen“ zeigt das Display automatisch die Auflösung: richtige Antwort markiert und Klassenverteilung. „Weiter →“ startet die nächste Frage. Nach der letzten Frage zeigt das Display die Gesamtpunkte aller 22 Schüler.


## v14 – vereinfachter Lehrerablauf
Der Unterrichtsbildschirm verwendet jetzt nur noch eine aktive Hauptaktion:
- **Bereit:** „Frage starten“
- **Scannen:** „Scannen beenden“
- **Auswertung:** „Nächste Frage“
- **Fertig:** Gesamtwertung auf dem Display

Display und iPhone bleiben als separate Geräte erhalten. Die Kamera des iPhones startet erst, wenn die aktuelle Frage vom Lehrer gestartet wurde.


## v15 – Start per Button oder Leertaste
Auf dem Lehrer-MacBook kann der Ablauf jetzt zusätzlich mit der **Leertaste** gesteuert werden: Bereit → Frage starten, Scannen → beenden, Auswertung → nächste Frage. Eingabefelder werden dabei nicht abgefangen.


## v16 – Lehrersteuerung vereinfacht
Der Lehrer-Spielmodus hat jetzt einen einzigen großen Aktionsbutton. Die Beschriftung und Farbe/Zustand erklären jederzeit den nächsten Schritt:
- 🟢 **BEREIT → FRAGE STARTEN**
- 🔵 **FRAGE LÄUFT → SCANNEN BEENDEN**
- 🟠 **AUSWERTUNG → NÄCHSTE FRAGE**
- 🎉 **QUIZ BEENDET**

Die Leertaste löst dieselbe Aktion aus.


## v17 – Ein-Klick-Unterricht
**🎮 Unterricht starten** im Administrator startet jetzt gleichzeitig Lehrerfenster und Display und setzt die erste Frage direkt auf „läuft“. Ein separater „Display öffnen“-Button und ein separater „Frage starten“-Schritt im Lehrerfenster sind nicht mehr nötig. Der Lehrer beendet die Scanphase und geht danach mit **„Nächste Frage“** weiter. Die Leertaste steuert Stoppen und Weiter.
