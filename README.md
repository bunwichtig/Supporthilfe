# Supporthilfe

Ein Werkzeug, das Supportern hilft, Probleme einer Software schnell zu lösen. Gefüllt wird es mit Support-Einträgen im JSON-Format. Die Beispieldaten beschreiben die erfundene Rechnungssoftware „Fakturo“ mit den Online-Modulen „Fakturo Zeit“, „Fakturo Rundgang“ und „Fakturo Wachbuch“.

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

Die Startseite zeigt eine Suche, 10 Hauptkategorien und 12 häufig gesuchte Themen. Nach einer Suche führen vier Fragestufen zur Antwort:

1. **Thema**
2. **Symptom**
3. **Umfang**
4. **Befund**

Jede Stufe wird gefragt, auch wenn es nur eine passende Antwort gibt (dann als Bestätigung). Passt keine Antwort, führt „Etwas anderes“ zu einem Ticket an den 2nd Level. Am Ende stehen Ursache, Prüfschritte, Lösung und ein Hinweis für den Support.

## Aufbau eines Eintrags

Pflichtfelder sind `id`, `name`, `kategorie` und `bezeichnung`. Alles Weitere steht in `zusatz`, unter anderem:

- `stufe1` bis `stufe4`: Antworten auf die vier Fragestufen
- `ursache`, `pruefen`, `loesung`, `hinweis`: mehrzeiliger Text mit `\n`
- `frage`, `stichworte`, `produkt` (`alle` passt zu jedem Produkt), `wann`, `geraet`, `betriebssystem`, `fehlercode`

`kategorie` enthält den ausführlichen Namen einer der 10 Kategorien aus `support-katalog.json`.

## Stand

Version 3 mit 71 Beispielfällen.
