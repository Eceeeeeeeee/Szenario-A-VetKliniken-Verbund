# Profiling-Report: praxis_juckstadt_behandlungen.csv

_Erstellt: 2026-06-07_

## Schritt 1 · Struktur

| Merkmal | Wert |
|---|---|
| Format | CSV |
| Trennzeichen | `;` |
| Encoding | UTF-8 |
| Header | ja |
| Zeilen | 150 |
| Spalten | 6 |
| Spaltenname | beh_nr, datum, patient_name, kunde_nachname, diagnose, kosten_euro |

## Schritt 2 · Wertebereiche

| Spalte | Typ-Vermutung | Beispiel | Distinct | Null% | Bemerkung |
|---|---|---|---:|---:|---|
| `beh_nr` | VARCHAR | 1 | 150 | 0.0% |  |
| `datum` | DATE | 2026-02-06 | 114 | 0.0% |  |
| `patient_name` | VARCHAR | Pumba | 32 | 0.0% |  |
| `kunde_nachname` | VARCHAR | Krueger | 38 | 0.0% |  |
| `diagnose` | VARCHAR | Augenuntersuchung | 19 | 0.0% |  |
| `kosten_euro` | VARCHAR | 191,17 | 150 | 0.0% |  |

**Kostenbereich:** Min 17.60 EUR – Max 197.30 EUR – Mittelwert 104.32 EUR
**Datumsbereich:** 2025-09-01 bis 2026-04-01

## Schritt 3 · Fehlwerte

| Spalte | Fehlwerte | Null% |
|---|---:|---:|
| `beh_nr` | 0 | 0.0% |
| `datum` | 0 | 0.0% |
| `patient_name` | 0 | 0.0% |
| `kunde_nachname` | 0 | 0.0% |
| `diagnose` | 0 | 0.0% |
| `kosten_euro` | 0 | 0.0% |

## Schritt 4 · Muster

| Feld | Muster | Auffälligkeiten |
|---|---|---|
| `beh_nr` | Ganzzahl als Text gespeichert | 0 doppelte Werte |
| `datum` | `YYYY-MM-DD` | 0 nicht parsebar |
| `patient_name` | Tiername als Text | 32 Ausprägungen |
| `kunde_nachname` | Kunden-Nachname als Text | kein technischer Fremdschlüssel zur Kundendatei |
| `diagnose` | Diagnose/Leistung als Text | 19 Ausprägungen |
| `kosten_euro` | deutsches Dezimalkomma, z. B. `191,17` | 0 auffällig |

## Schritt 5 · Auffälligkeiten

| Prüfung | Befund |
|---|---:|
| Vollständig doppelte Zeilen | 0 |
| Doppelte `beh_nr` | 0 |
| Nicht interpretierbare Datumswerte | 0 |
| Nicht numerisch interpretierbare Kosten | 0 |
| Kostenwerte mit falschem Muster | 0 |
| Betrags-Ausreißer nach IQR-Regel | 0 |

**Fazit:** Die Behandlungsdatei ist strukturell sauber einlesbar und enthält keine auffälligen Fehlwerte. Wichtig für spätere Verarbeitung ist, dass `kosten_euro` als Text mit deutschem Dezimalkomma vorliegt. Außerdem gibt es keinen technischen Fremdschlüssel zur Kundendatei; die Verbindung ist nur über `kunde_nachname` möglich und daher fachlich unsicher.
