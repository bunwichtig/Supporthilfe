# Supporthilfe

Ein internes Werkzeug für Supporter (1st und 2nd Level), das bei der Ticketbearbeitung schnell zum bekannten Fall und zur Antwort führt. Gefüllt wird es mit Support-Einträgen im JSON-Format. Die Beispieldaten beschreiben die erfundene Rechnungssoftware „Fakturo“ mit den Online-Modulen „Fakturo Zeit“, „Fakturo Rundgang“ und „Fakturo Wachbuch“.

## Inhalt

| Ordner | Inhalt |
| --- | --- |
| `mockup/` | `problemsuche.html`: klickbares Mockup der geführten Problemsuche. `beispieldaten.json`: die Einträge, mit denen das Mockup arbeitet. |
| `support-katalog/` | `support-katalog.json`: vollständiger Katalog (Programme, Kategorien, „Oft gesucht“, Einträge). Dazu `eintraege.json`, `eintraege.csv` und `kategorien.csv` (CSV mit `;` und UTF-8-BOM, für Excel). |
| `support-input/` | `support-eintrag.schema.json`: JSON-Schema für einen einzelnen Support-Eintrag. |

## Mockup ansehen

Online: https://bunwichtig.github.io/Supporthilfe/

Oder `mockup/problemsuche.html` lokal im Browser öffnen. Es braucht keinen Server.

## So funktioniert die Problemsuche

Die Startseite zeigt eine Suche (Ticketbetreff, Symptom oder Fehlercode), 10 Bereiche und 12 häufige Tickets. Nach einer Suche grenzen vier kurze Stufen auf den Fall ein:

1. **Thema**
2. **Symptom**
3. **Umfang**
4. **Befund**

Jede Stufe wird gefragt, auch wenn nur eine Antwort passt (dann als Abgleich mit dem Ticket). „Unklar“ überspringt eine Stufe, „Anderes“ führt zur Übergabe an den 2nd Level mit vorausgefülltem Pfad.

Ein Fall zeigt in dieser Reihenfolge, knapp und in Fachsprache:

1. **Kurzdiagnose**
2. **Lösung** als Schritte mit Menüpfaden
3. **Rückfragen an den Kunden**, falls im Ticket Angaben fehlen
4. **Textbaustein** für die Antwortmail (Sie-Form, mit Kopieren-Knopf, Rückfragen optional anhängen)
5. **Eskalation**: wann und an wen
6. **Begründung** ganz unten: warum das passiert

## Aufbau eines Eintrags

Pflichtfelder sind `id`, `name`, `kategorie` und `bezeichnung` (= Kurzdiagnose, eine Zeile). Alles Weitere steht in `zusatz`, unter anderem:

- `stufe1` bis `stufe4`: Antworten auf die vier Stufen
- `loesung`, `rueckfragen`: mehrzeiliger Text mit `\n`
- `textbaustein`: Antworttext an den Kunden, ohne Anrede und Gruß
- `eskalation`, `begruendung`
- `frage`, `stichworte`, `produkt` (`alle` passt zu jedem Produkt), `wann`, `geraet`, `betriebssystem`, `fehlercode`

`kategorie` enthält den ausführlichen Namen einer der 10 Kategorien aus `support-katalog.json`.

## Stand

Version 4 mit 71 Beispielfällen, ausgerichtet auf Supporter bei der Ticketbearbeitung.
