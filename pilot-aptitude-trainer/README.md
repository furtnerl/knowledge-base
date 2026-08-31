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

## Abdeckung der DLR-Berufsgrunduntersuchung

Die öffentlich dokumentierten Untertests der DLR-BU und ihre Entsprechung im Trainer:

| Kürzel | Untertest | Modul |
|---|---|---|
| KRN | Kopfrechnen | Kopfrechnen |
| TVT | Technisches Verständnis | Technisches Verständnis |
| ENS | Englischtest | Englisch |
| VMC | Visuelle Merkfähigkeit | Merkfähigkeit |
| RMS | Running Memory Span (akustisch) | Akustisches Gedächtnis |
| PPT | Würfelklappen | Würfelklappen |
| WFG | Wegfigurentest | Wegfiguren |
| ROT | Rotation / räumliche Orientierung | Räumliche Orientierung |
| OWT | Optischer Wahrnehmungstest | Optische Wahrnehmung |
| SKT | Dreieckstest | Dreieckstest |
| MIC | Multitasking / Instrumentenkoordination | Multitasking (siehe Einschränkung) |

**Bewusst nicht abgebildet.** Der MIC wird im Original mit Joystick und Schubhebel
geflogen; hier läuft der Kanal über Tastatur beziehungsweise Bildschirmtasten. Die
Anforderung an die Aufmerksamkeitsverteilung bleibt, die feinmotorische Komponente
fehlt. Die Firmenqualifikation (FQ) – Gruppenübungen, Interviews, Verhaltens­beobachtung
und der IFR-Simulatorflug – ist ein Assessment-Center mit realen Beteiligten und
lässt sich in einer Web-App grundsätzlich nicht nachbilden.

**Ergänzend, kein benannter DLR-Untertest.** Instrumentenablesen, Linienverfolgung,
Konzentration (d2-Prinzip) und Logisches Denken. Diese Aufgabentypen kommen in
anderen Auswahlverfahren der Branche vor und trainieren verwandte Fähigkeiten.

## Module

| Modul | Getestet wird | Umsetzung |
|---|---|---|
| Kopfrechnen | Zahlensicherheit unter Zeitdruck | 13 Aufgabengeneratoren: Zeit-Weg-Geschwindigkeit, Treibstoff, 3:1-Sinkprofil, Einheiten, Windkomponenten, ISA, Höhenmesser, Zahlenreihen |
| Technisches Verständnis | Physik und Flugzeugsysteme | Fragenpool zu Mechanik, Fluiden, Elektrik, Aerodynamik, Systemen – je mit Lösungsweg |
| Englisch | Wortschatz, Grammatik, Leseverständnis | Fragenpool inkl. Fließtextaufgaben und Standard-Sprechgruppen |
| Würfelklappen | Räumliches Vorstellungsvermögen | Neun geprüfte Würfelnetze, exakt gefaltet; die Zeichen sind lagerichtig, Antworten unterscheiden sich teils nur in der Drehung |
| Wegfiguren | Räumliche Umorientierung | Prozedural erzeugte, überschneidungsfreie Wege; Kurven zählen aus Sicht des Fahrenden |
| Räumliche Orientierung | Fluglagen aus dem künstlichen Horizont | Auf Canvas gezeichneter Horizont und Flugzeugsilhouetten von hinten, in beiden Richtungen abgefragt |
| Merkfähigkeit | Kurzzeitgedächtnis für strukturierte Daten | Zufällig erzeugter Abflugplan, Lernphase mit Zeitlimit, anschließende Abfrage aller Spalten |
| Akustisches Gedächtnis | Akustisches Arbeitsgedächtnis | Vorgelesene Ziffernfolgen unbekannter Länge, die letzten Ziffern rückwärts eingeben; stille Darstellung als Rückfallebene |
| Optische Wahrnehmung | Selektive Wahrnehmung | Uhrentafel mit kurzer Standzeit, nur Uhren einer Form und Helligkeit zählen |
| Dreieckstest | Daueraufmerksamkeit und Regeltreue | Fortlaufende Dreiecke, zwei gemerkte Vergleichsregeln, drei Antworttasten |
| Konzentration | Sorgfalt über Belastungsdauer | Zeichenfeld nach d2-Prinzip, Fehlklicks werden negativ gewertet |
| Linienverfolgung | Visuelle Verfolgung | Prozedural erzeugte, sich kreuzende Linienbündel als SVG |
| Instrumentenablesen | Analoge Rundinstrumente | Fahrtmesser, Höhenmesser, Kurskreisel, Variometer, Wendezeiger und kompletter Six-Pack-Scan |
| Logisches Denken | Regeln erkennen, formal schließen | Zahlen- und Buchstabenreihen, Figurenmatrizen, Syllogismen |
| Multitasking | Aufmerksamkeitsverteilung | Drei parallele Kanäle: Kurshaltung, Systemüberwachung, Kopfrechnen – getrennt und gewichtet bewertet |

Dazu kommt eine **Prüfungssimulation** – kurz (sechs Module) oder vollständig
(alle fünfzehn) –, die die Module ohne Rückmeldung hintereinander durchlaufen lässt und am Ende eine Gesamtauswertung mit Empfehlung
für den nächsten Trainingsschwerpunkt erstellt.

## Bedienung

- Antworten per Klick oder mit den Tasten `1`–`4`, weiter mit `Enter`
- Abbruch jederzeit mit `Esc`
- Multitasking: Pfeiltasten oder `W A S D` für die Kurshaltung, `1`–`4` für
  Systemwarnungen, `G` / `U` für die Rechenaufgabe; auf Touchgeräten über die
  Bildschirmtasten
- Dreieckstest: `A` / `S` / `D` für die drei Antworten
- Akustisches Gedächtnis: Zifferntasten, `Rücktaste`, `Enter`
- Drei Schwierigkeitsstufen steuern Zeitlimits und Aufgabenniveau
- Tag- und Nachtdarstellung über die Schaltfläche rechts oben

## Technik

Reines HTML, CSS und JavaScript ohne Abhängigkeiten. Instrumente, Würfel,
Uhrentafeln, Wegfiguren und der Multitasking-Kanal werden auf `<canvas>` gezeichnet,
die Linienverfolgung als SVG erzeugt. Die Würfelnetze werden über die tatsächliche
Faltgeometrie ausgewertet (Flächennormale plus Aufrichtung je Feld), sodass auch die
Drehung der Zeichen stimmt; ungültige Netze werden zur Laufzeit ausgefiltert. Das
akustische Gedächtnis nutzt `speechSynthesis` und fällt bei fehlender Sprachausgabe
automatisch auf eine stille Darstellung zurück. Ergebnisse liegen ausschließlich in `localStorage` des jeweiligen
Browsers; verweigert der Browser den Zugriff, läuft das Training weiter, nur ohne
gespeicherten Verlauf.

## Hinweis

Unabhängiges, privates Übungswerkzeug. Es steht in keiner Verbindung zu Austrian
Airlines oder einem anderen Luftfahrtunternehmen und bildet kein offizielles
Testverfahren ab. Aufbau und Aufgabentypen orientieren sich an den öffentlich
beschriebenen, im deutschsprachigen Raum üblichen fliegerischen Eignungsverfahren.
Inhalt, Umfang und Ablauf des tatsächlichen Auswahlverfahrens können davon
abweichen – verbindlich sind ausschließlich die Angaben des Unternehmens.
