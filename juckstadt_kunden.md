# Profiling-Report: praxis_juckstadt_kunden.csv

_Erstellt: 2026-06-07_

## Schritt 1 · Struktur

| Merkmal | Wert |
|---|---|
| Format | CSV |
| Trennzeichen | `;` |
| Encoding | UTF-8 |
| Header | ja |
| Zeilen | 223 |
| Spalten | 10 |
| Spaltenname | kunden_nr, anrede, vorname, nachname, strasse, plz, ort, telefon, email, angelegt_am |

## Schritt 2 · Wertebereiche

| Spalte | Typ-Vermutung | Beispiel | Distinct | Null% | Bemerkung |
|---|---|---|---:|---:|---|
| `kunden_nr` | VARCHAR | 1 | 223 | 0.0% |  |
| `anrede` | VARCHAR | Herr | 2 | 0.0% |  |
| `vorname` | VARCHAR | Thomas | 63 | 0.0% |  |
| `nachname` | VARCHAR | Berger | 43 | 0.0% |  |
| `strasse` | VARCHAR | Hauptstr. 12 | 214 | 0.0% |  |
| `plz` | VARCHAR | 35500 | 8 | 0.0% |  |
| `ort` | VARCHAR | Juckstadt | 10 | 0.0% |  |
| `telefon` | VARCHAR | 06450-1234 | 222 | 0.0% |  |
| `email` | VARCHAR | berger@email.de | 197 | 9.4% |  |
| `angelegt_am` | DATE | 2021-05-12 | 215 | 0.0% |  |

## Schritt 3 · Fehlwerte

| Spalte | Fehlwerte | Null% |
|---|---:|---:|
| `kunden_nr` | 0 | 0.0% |
| `anrede` | 0 | 0.0% |
| `vorname` | 0 | 0.0% |
| `nachname` | 0 | 0.0% |
| `strasse` | 0 | 0.0% |
| `plz` | 0 | 0.0% |
| `ort` | 0 | 0.0% |
| `telefon` | 0 | 0.0% |
| `email` | 21 | 9.4% |
| `angelegt_am` | 0 | 0.0% |

## Schritt 4 · Muster

| Feld | Muster | Auffälligkeiten |
|---|---|---|
| `kunden_nr` | Ganzzahl als Text gespeichert | 0 doppelte Werte |
| `anrede` | `Herr` / `Frau` | 2 Ausprägungen |
| `plz` | 5-stellig | 0 auffällig |
| `telefon` | lokales Format mit Bindestrich, z. B. `06450-1234` | 0 auffällig |
| `email` | `xxx@xxx.xxx` | 21 fehlend, 0 ungültig |
| `angelegt_am` | `YYYY-MM-DD` | 0 nicht parsebar |

## Schritt 5 · Auffälligkeiten

| Prüfung | Befund |
|---|---:|
| Vollständig doppelte Zeilen | 0 |
| Doppelte `kunden_nr` | 0 |
| Doppelte Telefonnummern | 2 |
| Fehlende E-Mail-Adressen | 21 |
| Ungültige E-Mail-Formate | 0 |
| Ungültige PLZ-Formate | 0 |
| Nicht interpretierbare Datumswerte | 0 |

**Fazit:** Die Kundendatei ist strukturell sauber einlesbar. Kritisch für spätere Integrations- und Matching-Schritte sind vor allem fehlende E-Mail-Adressen und mögliche Dubletten bei Telefonnummern. Die Spalten `kunden_nr`, `plz` und `angelegt_am` wirken anhand der Profiling-Prüfungen formal konsistent.
