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
