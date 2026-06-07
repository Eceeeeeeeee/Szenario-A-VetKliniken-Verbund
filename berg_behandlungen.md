# Profiling: praxis_bergblick_export.xml – Behandlungen

_Erstellt: 2026-06-07_

## Datei
- Format: XML, gleiche Quelldatei wie Patienten/Halter/Tiere
- Namespace: `http://vetkliniken-hessen.de/schema/v2`
- Encoding: UTF-8
- Header: nein, XML-Struktur
- Zeilen Behandlungen: 150
- Spalten nach Flattening: 11

## Fachliche Einordnung
Die Behandlungen aus Bergblick sind separat innerhalb der XML-Datei gespeichert. Sie referenzieren Patienten über `patientId`. Das Datum liegt als Attribut vor. Die Kosten sind als Netto- und Bruttobetrag getrennt gespeichert.

## Spalten

| Spalte            | Typ-Vermutung   | Beispiel           |   Distinct | Null%   | Bemerkung   |
|:------------------|:----------------|:-------------------|-----------:|:--------|:------------|
| xml_position      | NUMERIC         | 1                  |        150 | 0.0%    |             |
| behandlung_id     | VARCHAR         | –                  |          0 | 100.0%  |             |
| patient_id        | VARCHAR         | P-4191             |        115 | 0.0%    |             |
| datum             | DATE            | 2025-11-15         |        111 | 0.0%    |             |
| diagnose          | VARCHAR         | Tumorabklaerung    |         19 | 0.0%    |             |
| leistung          | VARCHAR         | –                  |          0 | 100.0%  |             |
| kosten_netto      | NUMERIC         | 162.92             |        150 | 0.0%    |             |
| kosten_brutto     | NUMERIC         | 193.87             |        150 | 0.0%    |             |
| kosten_netto_num  | NUMERIC         | 162.92             |        150 | 0.0%    |             |
| kosten_brutto_num | NUMERIC         | 193.87             |        150 | 0.0%    |             |
| steuer_faktor     | NUMERIC         | 1.1899705376872085 |        149 | 0.0%    |             |

## Ergebnisinterpretation
Das Profiling zeigt, dass die zentralen Behandlungsinformationen vollständig extrahiert werden konnten. `patient_id`, `datum`, `diagnose`, `kosten_netto` und `kosten_brutto` sind vorhanden. Es gibt keine verwaisten Behandlungsreferenzen, d. h. jede Behandlung verweist auf eine vorhandene Patient-ID. Die Beträge sind numerisch interpretierbar und die Brutto-/Netto-Logik ist plausibel.

Auffällig ist, dass keine explizite Behandlungs-ID vorliegt. Für die Pipeline sollte deshalb eine technische ID oder die XML-Position als Provenance-Merkmal genutzt werden.

## Auffällige Muster
- `patientId` liegt als Attribut der Behandlung vor.
- `datum` liegt ebenfalls als Attribut vor.
- Die Behandlungssumme ist in Netto- und Bruttobetrag aufgeteilt.
- Netto und Brutto liegen als Attribute des `summe`-Elements vor.
- Eine naive Element-Extraktion würde diese Werte verlieren und später künstliche Rejects erzeugen.
- Keine explizite Behandlungs-ID vorhanden; technische ID aus `xml_position` sinnvoll.

## Datenqualitätsprobleme

| kategorie       | quelle            | feld                       |   anzahl | beschreibung                                                                                                                                       |
|:----------------|:------------------|:---------------------------|---------:|:---------------------------------------------------------------------------------------------------------------------------------------------------|
| Encoding/Parser | berg_export       | Namespace                  |        1 | XML verwendet einen Namespace; Parser/XPath-Abfragen müssen namespace-aware umgesetzt werden.                                                      |
| Fehlwerte       | berg_behandlungen | patient_id                 |        0 | Behandlung ohne Patient-ID kann keinem Patienten/Halter/Tier zugeordnet werden.                                                                    |
| Referenz        | berg_behandlungen | patient_id                 |        0 | Behandlungen verweisen auf Patient-IDs, die in den Patientendaten nicht vorkommen.                                                                 |
| Schema/Struktur | berg_behandlungen | behandlung_id              |      150 | Die Quelle liefert keine bzw. nicht durchgängig explizite Behandlungs-ID; xml_position muss als technische Zeilennummer/Provenance genutzt werden. |
| Dubletten       | berg_behandlungen | behandlung_id              |        0 | Nicht-leere Behandlungs-IDs kommen mehrfach vor; das wäre für eindeutige Behandlungen auffällig.                                                   |
| Fehlwerte       | berg_behandlungen | datum                      |        0 | Behandlungsdatum fehlt; spätere Normalisierung und Zeitbezug wären nicht möglich.                                                                  |
| Format          | berg_behandlungen | datum                      |        0 | Behandlungsdatum weicht vom ISO-Format YYYY-MM-DD ab.                                                                                              |
| Format          | berg_behandlungen | kosten_netto               |        0 | kosten_netto ist nicht numerisch interpretierbar.                                                                                                  |
| Format          | berg_behandlungen | kosten_brutto              |        0 | kosten_brutto ist nicht numerisch interpretierbar.                                                                                                 |
| Semantik        | berg_behandlungen | kosten_netto/kosten_brutto |        0 | Bruttobetrag ist kleiner als Nettobetrag; das wäre fachlich auffällig.                                                                             |

## Bewertung für die Pipeline
Für Bergblick ist besonders wichtig, dass der XML-Parser sowohl Elemente als auch Attribute ausliest. Andernfalls würden Patient-Referenzen, Behandlungsdatum und Kostenbeträge fehlen. Das würde in der Transform-Schicht fälschlich als Datenqualitätsproblem erscheinen. Inhaltlich sind die Behandlungsdaten stabil; technisch muss jedoch eine eigene technische ID erzeugt werden.
