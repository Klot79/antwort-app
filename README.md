# Antwort! v4 – komplett neu, zwei Bereiche

- `index.html` = Administratorbereich: Fragen auf 3 Wegen erstellen, Karten drucken, Schüler verwalten, Scanner und Statistiken.
- `display.html` = Displaybereich für die Klasse: vollständige Frage, vier Antworten, Karten-Zähler und Lehrersteuerung **Start / Weiter / Überspringen**.

## Spielablauf
1. **Start** zeigt die aktuelle Frage.
2. Im Adminbereich werden Karten gescannt. Oben rechts im Display steht jederzeit die Zahl der gescannten Karten.
3. **Weiter** beendet die Frage und zeigt die Gesamtresultate.
4. **Weiter** im Ergebnisbild startet die nächste Frage.
5. **Überspringen** geht sofort zur nächsten Frage, ohne auf alle Karten zu warten und ohne Ergebnisanzeige.

Die Synchronisation zwischen Admin und Display erfolgt über `localStorage` im selben Browser/Gerät. Für ein Display auf einem anderen Gerät braucht es später eine kleine Realtime-Serververbindung.
