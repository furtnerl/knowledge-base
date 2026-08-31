# Flight Deck Selection Trainer

Web-App zum Training fliegerischer Aufnahmetests, ausgelegt auf die Vorbereitung
auf das Auswahlverfahren für Verkehrspilotinnen und -piloten (Austrian Airlines
und andere Betreiber im deutschsprachigen Raum).

## Starten

Die App ist eine einzelne, in sich geschlossene HTML-Datei ohne Build-Schritt und
ohne Server-Abhängigkeit:

```
open pilot-aptitude-trainer/index.html      # macOS
xdg-open pilot-aptitude-trainer/index.html  # Linux
```

Alternativ über einen lokalen Server:

```
python3 -m http.server -d pilot-aptitude-trainer 8000
# http://localhost:8000
```

Externe Ressource ist ausschließlich Google Fonts. Ohne Internetverbindung greifen
die im CSS hinterlegten System-Fallbacks; die App bleibt vollständig funktionsfähig.

## Module

| Modul | Getestet wird | Umsetzung |
|---|---|---|
| Kopfrechnen | Zahlensicherheit unter Zeitdruck | 13 Aufgabengeneratoren: Zeit-Weg-Geschwindigkeit, Treibstoff, 3:1-Sinkprofil, Einheiten, Windkomponenten, ISA, Höhenmesser, Zahlenreihen |
| Technisches Verständnis | Physik und Flugzeugsysteme | Fragenpool zu Mechanik, Fluiden, Elektrik, Aerodynamik, Systemen – je mit Lösungsweg |
| Englisch | Wortschatz, Grammatik, Leseverständnis | Fragenpool inkl. Fließtextaufgaben und Standard-Sprechgruppen |
| Merkfähigkeit | Kurzzeitgedächtnis für strukturierte Daten | Zufällig erzeugter Abflugplan, Lernphase mit Zeitlimit, anschließende Abfrage aller Spalten |
| Räumliche Orientierung | Fluglagen aus dem künstlichen Horizont | Auf Canvas gezeichneter Horizont und Flugzeugsilhouetten von hinten, in beiden Richtungen abgefragt |
| Instrumentenablesen | Analoge Rundinstrumente | Fahrtmesser, Höhenmesser, Kurskreisel, Variometer, Wendezeiger und kompletter Six-Pack-Scan |
| Konzentration | Daueraufmerksamkeit und Sorgfalt | Zeichenfeld nach d2-Prinzip, Fehlklicks werden negativ gewertet |
| Wegverfolgung | Visuelle Verfolgung | Prozedural erzeugte, sich kreuzende Linienbündel als SVG |
| Multitasking | Aufmerksamkeitsverteilung | Drei parallele Kanäle: Kurshaltung, Systemüberwachung, Kopfrechnen – getrennt und gewichtet bewertet |

Dazu kommt eine **Prüfungssimulation**, die mehrere Module ohne Rückmeldung
hintereinander durchlaufen lässt und am Ende eine Gesamtauswertung mit Empfehlung
für den nächsten Trainingsschwerpunkt erstellt.

## Bedienung

- Antworten per Klick oder mit den Tasten `1`–`4`, weiter mit `Enter`
- Abbruch jederzeit mit `Esc`
- Multitasking: Pfeiltasten oder `W A S D` für die Kurshaltung, `1`–`4` für
  Systemwarnungen, `G` / `U` für die Rechenaufgabe; auf Touchgeräten über die
  Bildschirmtasten
- Drei Schwierigkeitsstufen steuern Zeitlimits und Aufgabenniveau
- Tag- und Nachtdarstellung über die Schaltfläche rechts oben

## Technik

Reines HTML, CSS und JavaScript ohne Abhängigkeiten. Instrumente und der
Multitasking-Kanal werden auf `<canvas>` gezeichnet, die Wegverfolgung als SVG
erzeugt. Ergebnisse liegen ausschließlich in `localStorage` des jeweiligen
Browsers; verweigert der Browser den Zugriff, läuft das Training weiter, nur ohne
gespeicherten Verlauf.

## Hinweis

Unabhängiges, privates Übungswerkzeug. Es steht in keiner Verbindung zu Austrian
Airlines oder einem anderen Luftfahrtunternehmen und bildet kein offizielles
Testverfahren ab. Aufbau und Aufgabentypen orientieren sich an den öffentlich
beschriebenen, im deutschsprachigen Raum üblichen fliegerischen Eignungsverfahren.
Inhalt, Umfang und Ablauf des tatsächlichen Auswahlverfahrens können davon
abweichen – verbindlich sind ausschließlich die Angaben des Unternehmens.
