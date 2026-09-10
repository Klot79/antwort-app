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


## v25 – finale Kartenansicht
- **Jedes Kind einzeln auf einer eigenen A4-Seite.**
- Kartenlayout entspricht dem gewünschten Referenzdesign.
- Vier schwarze Eck-Finder bleiben erhalten.
- QR-Code wird technisch mit **600 × 600 Pixel** erzeugt.
- A/B/C/D stehen außerhalb des QR-Codes und sind nicht Teil des QR-Codes.
- Die vier möglichen Drehungen sind für die 22 Karten korrekt verteilt:
  - A oben / B rechts / C unten / D links
  - B oben / D rechts / C unten / A links
  - C oben / B rechts / A unten / D links
  - D oben / A rechts / C unten / B links
- Name und Emoji werden aus den Schülerdaten übernommen und bleiben im Administrator editierbar.
- Keine zusätzliche leere Druckseite nach der letzten Karte.


## v26 – Karten exakt nach Referenzdesign
- Hochformat A4.
- Abgerundeter schwarzer Rahmen.
- Keine kleinen Eck-Rechtecke/Finder.
- Kleines Emoji oben, darunter Name und E-ID.
- QR-Code mittig und deutlich größer.
- QR-Code wird technisch exakt mit **600 × 600 Pixel** erzeugt.
- A/B/C/D liegen außerhalb des QR-Codes mit ausreichend Abstand.
- Vier Orientierungen wechseln korrekt für das Drehen der Karte.
- 22 Kinder = 22 einzelne A4-Seiten.
- Namen bleiben im Administrator editierbar und werden automatisch auf die Karten übernommen.
- Keine zusätzliche Leerseite nach der letzten Karte.


## v29 – Drucklayout technisch korrigiert
- Ursache des Leerseiten-Problems beseitigt: kein `page-break-after` mehr auf jeder Karte.
- Seitenumbruch erfolgt ausschließlich **vor jeder Karte außer der ersten**.
- Jede Druckseite ist bewusst 296 mm hoch, damit keine Rundungs-/Überlaufseite entsteht.
- QR-Code ist tatsächlich **90 × 90 mm** auf dem Ausdruck und wird mit **600 × 600 Pixel** gerendert.
- A/B/C/D liegen außerhalb des QR-Codes.
- Eck-Finder sind entfernt, entsprechend dem bestätigten Referenzdesign.


## v29 – Druckproblem endgültig behoben
- Druck wird in einem **eigenen, reinen Druckfenster** erzeugt; die Administratoroberfläche kann dadurch keine zusätzlichen Seiten mehr verursachen.
- Es gibt keinen `page-break-after` mehr, der nach der letzten Karte eine Leerseite erzeugt.
- Der Seitenumbruch liegt ausschließlich **vor Karte 2, 3, 4 ...**.
- QR-Code: **600 × 600 Pixel** Renderauflösung und **90 × 90 mm** tatsächliche Druckfläche.
- A/B/C/D sind vollständig außerhalb des QR-Codes.


## v30 – Top 5 öffentlich, vollständige Lehrkraft-Auswertung
- Gesamtergebnis auf Mac/Display zeigt **nur die ersten 5** mit Platzierung, Emoji und Punkten.
- Namen erscheinen dort nicht.
- Administrator > Statistiken zeigt weiterhin **alle 22 Schüler mit Namen**.
- Zusätzlich: Gesamtpunkte, richtig, beantwortete Fragen und Quote für die spätere Förderung.


## v31 – Jubel-Abschlussbildschirm
- Das neue Jubel-/Feier-Design wird als Hintergrund für das Gesamtergebnis verwendet.
- Die Top-5-Daten bleiben dynamisch und werden über dem Design eingeblendet.
- Öffentlich weiterhin nur **Platzierung, Emoji und Punkte**, keine Namen.
- Grüner Home-Button führt zurück zum Administrator.
- Mac-Spielsteuerung und AirPlay-Display verwenden denselben Abschlussstil.


## v32 – finales Abschlussbild
- Das vom Benutzer ausgewählte Jubelbild wird **ganz am Ende des Quiz** als vollständiger Abschlussbildschirm verwendet.
- Es ersetzt die bisherige schlichte Gesamtbewertung.
- Die Top-5-Platzierung bleibt dynamisch: Emoji, Platz und Punkte werden aus dem Quiz-Ergebnis eingesetzt.
- Keine Schülernamen auf dem öffentlichen Abschlussbild.
- Der Home-Button bleibt vorhanden.


## v33 – Abschlussbild korrekt zentriert
- Das Jubelbild liegt im Mac-Steuerungsfenster **zentral im großen Hauptbereich**.
- Die rechte Spalte enthält **ausschließlich** den Button „Zurück zum Administrator“.
- Der im Bild vorhandene alte Home-Button wurde aus der verwendeten Hintergrundfassung entfernt, damit er nicht doppelt erscheint.
- Das AirPlay-Display zeigt das Jubelbild **vollflächig und zentriert** ohne Lehrer-Button.
- Top-5-Platzierung, Emoji und Punkte bleiben dynamisch.


## v34 – Abschlussfehler behoben
- Ursache behoben: Der Abschlussrenderer griff auf ein nicht vorhandenes Element `control` zu und brach deshalb vor dem Anzeigen des Jubelbildes ab.
- Der Renderer prüft jetzt alle Elemente sicher, bevor er sie verändert.
- Das Jubelbild wird am Ende zuverlässig in den großen Hauptbereich eingesetzt.
- Rechts bleibt ausschließlich der Home-Button.


## v35 – keine doppelte Siegerbewertung
- Ursache gefunden: Das Jubelbild selbst enthielt bereits eine statische Beispiel-Top-5.
- Darüber wurde zusätzlich die echte, dynamische Top-5 gelegt – dadurch erschien die Siegerbewertung doppelt.
- Das Hintergrundbild wurde deshalb technisch bereinigt: Die statischen Top-5-Zeilen wurden entfernt.
- Jetzt wird **nur noch die echte dynamische Top-5** angezeigt.
- Die rechte Spalte enthält weiterhin nur den Home-Button.


## v36 – finales Jubelbild passend eingebaut
- Das neue Jubelbild wurde als offizieller Abschluss-Hintergrund übernommen.
- Die dynamische Top-5 liegt **direkt unter dem Pokal** an der vorgesehenen Stelle.
- Die Ergebniszeilen sind vollständig deckend, damit keine statische Beispielwertung aus dem Bild durchscheint.
- Rechts im Mac-Steuerungsfenster bleibt ausschließlich der Home-Button.
- Im AirPlay-Display gibt es keinen Home-Button.


## v37 – Top-5-Überlappung behoben
- Ursache: Die dynamische Top-5 war gegenüber den fünf weißen Ergebnisfeldern im Hintergrund zu weit nach oben verschoben.
- Die Live-Ergebniszeilen werden jetzt exakt auf die vorgesehenen Karten des Jubelbildes gelegt.
- Dadurch ist nur noch **eine** sichtbare Platzierung vorhanden.
- Die tatsächlichen Punkte bleiben dynamisch.


## v38 – statische Platzierungen aus dem Abschlussbild entfernt
- Die fünf im Hintergrundbild fest eingebauten Platzierungsfelder wurden entfernt.
- Pokal, Banner, Jubel, Konfetti und die übrige Gestaltung bleiben erhalten.
- Die Top-5 wird ausschließlich durch die echte, dynamische Quiz-Auswertung erzeugt.
- Dadurch kann keine zweite Platzierung mehr durch das Bild durchscheinen.


## v39 – Abschlussbild vereinfacht
- Es gibt jetzt **nur noch eine** Abschlussgrafik: `abschluss.png`.
- Die fest eingebauten Beispiel-Platzierungen wurden nicht kompliziert aus dem Bild retuschiert.
- Stattdessen liegt unter dem Banner „Die Top 5“ ein sauberer weißer Bereich.
- Die echte Top-5 wird ausschließlich dynamisch von der App darübergelegt.
- Alte/doppelte Abschlussgrafiken wurden aus dem Paket entfernt.

## v40 – Karten und Scan-Rückmeldung
- Alle 22 Karten verwenden jetzt exakt dieselbe Orientierung: **A oben, B rechts, C unten, D links**.
- Der QR-Code bleibt die persönliche Karten-ID; die Antwort wird weiterhin aus der Drehung der Karte erkannt.
- Während des Scannens zeigt die Mac-Steuerung bei jeder erkannten Karte nur **👍 Karte gescannt**.
- Es wird dabei weder im Live-Feedback noch im Scan-Hinweis „richtig“ oder „falsch“ angezeigt.
- Das AirPlay-Display zeigt bei einer neu erkannten Karte kurz ein großes **👍**.
- Die Auflösungs-/Ergebnisphase bleibt für die vom Lehrer ausgelöste Auswertung erhalten.
