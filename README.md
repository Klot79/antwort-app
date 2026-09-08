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


## v18 – vereinfachter Unterrichtsablauf
Der Mac ist die einzige Steuerung und kann direkt per AirPlay gespiegelt werden. Das separate Display ist für den Ablauf nicht erforderlich.
1. Fragen vorher im Administrator erstellen.
2. **Unterricht starten** öffnet den großen Lehrerbildschirm.
3. iPhone mit dem angezeigten Raumcode verbinden.
4. **Scannen starten** – erst jetzt startet die iPhone-Kamera.
5. **Weiter – Ergebnis** – Auswertung/Klassenstatistik.
6. **Weiter – nächste Frage** – nächste Frage und neue Scanrunde.
7. Nach der letzten Frage wird die Gesamtwertung angezeigt.
Die Leertaste löst jeweils die aktuelle Hauptaktion aus.


## v19 – MacBook als Steuerung und Anzeige
Der MacBook-Spielmodus ist jetzt die zentrale Unterrichtsoberfläche. Es gibt keine Display-Steuerung mehr und keinen separaten Display-Button im Spielablauf. Der Mac zeigt Frage und Antworten groß an und steuert den kompletten Ablauf:
1. Unterricht starten
2. iPhone mit Raumcode verbinden
3. **Scannen starten**
4. **Weiter – Ergebnis**
5. **Weiter – nächste Frage**
6. am Ende **Gesamtergebnis**

Das iPhone dient ausschließlich zum Scannen der Kinderkarten.


## v20 – Abschluss, Statistik und Karten-QR
- Am Quizende zeigt der Unterrichtsbildschirm nur **Emoji + Punkte**, niemals die Namen der Kinder.
- Eine zufällige motivierende Abschlussnachricht wird eingeblendet.
- Ein **🏠 Zurück zum Administrator**-Button beendet die Unterrichtsansicht.
- In den Administrator-Statistiken bleiben die **Namen + Emoji** sichtbar.
- Der QR-Code auf den gedruckten Karten wurde auf **450 × 450 px** vergrößert (3× gegenüber 150 × 150).
- Ein erfolgreich erkannter Scan zeigt auf dem iPhone immer kurz **👍**; die Bewertung wird weiterhin am Mac mit 👍 richtig bzw. ❌ falsch angezeigt.


## v21 – QR 700 px und Druckfehler behoben
- QR-Code der Kinderkarten auf **700 × 700 px** vergrößert.
- Drucklayout so angepasst, dass jede Karte genau auf einer A4-Seite beginnt.
- Keine künstliche zusätzliche Leerseite nach der letzten Karte.
- Druckseiten verwenden saubere `break-before/page-break-before` Regeln.


## v23 – Rahmen beibehalten + QR 600 px + A/B/C/D
- Ausgangsbasis ist die **Version mit Kartenrahmen**.
- QR-Code wird intern mit **600 × 600 Pixeln** erzeugt.
- Rahmen und übriges Kartenlayout bleiben erhalten.
- Die Antwortflächen sind mit **A, B, C und D** gekennzeichnet.


## v24 – Kartenlayout nach dem gewünschten Design
- Kartenrahmen bleibt erhalten.
- Die vier kleinen Eck-Rechtecke/Finder sind entfernt.
- A/B/C/D stehen sauber und mittig **um** den QR-Code.
- Emoji ist gegenüber der bisherigen Version deutlich kleiner.
- Name und E-ID bleiben auf der Karte.
- Die Namen können im Administrator weiterhin pro Kind ergänzt/geändert werden.
- QR-Code wird mit **600 × 600 Pixel** erzeugt; seine physische Kartengröße bleibt kompakt.
- Jede Karte bleibt eine eigene A4-Seite; die letzte Karte erzeugt keine zusätzliche Leerseite.
