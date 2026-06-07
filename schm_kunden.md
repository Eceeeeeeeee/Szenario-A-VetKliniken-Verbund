# Profiling-Report: praxis_schmidt_kunden.csv

_Erstellt: 2026-06-07_

## Schritt 1 · Struktur

| Merkmal | Wert |
|---|---|
| Format | CSV |
| Trennzeichen | `|` (Pipe) |
| Encoding | UTF-8 |
| Header | ja |
| Zeilen | 234 |
| Spalten | 10 |
| Spaltenname | nachname, vorname, anrede, plz, ort, strasse, tel, email, erfasst, erfasst_year |

## Schritt 2 · Wertebereiche

| Spalte | Typ-Vermutung | Beispiel | Distinct | Null% | Bemerkung |
|---|---|---|---:|---:|---|
| `nachname` | VARCHAR | Berger | 45 | 0.0% |  |
| `vorname` | VARCHAR | Th. | 68 | 0.0% |  |
| `anrede` | VARCHAR | Hr. | 2 | 0.0% |  |
| `plz` | VARCHAR | 35500 | 8 | 0.0% |  |
| `ort` | VARCHAR | Juckstadt | 11 | 0.0% |  |
| `strasse` | VARCHAR | Hauptstr. 12 | 225 | 0.0% |  |
| `tel` | VARCHAR | 0645 01234 | 232 | 0.0% |  |
| `email` | VARCHAR | berger@email.de | 206 | 9.8% |  |
| `erfasst` | DATE | 06.12.2020 | 224 | 0.0% |  |
| `erfasst_year` | INTEGER | 2020 | 9 | 0.0% |  |

## Schritt 3 · Fehlwerte

| Spalte | Fehlwerte | Null% |
|---|---:|---:|
| `email` | 23 | 9.8% |
| Alle anderen Spalten | 0 | 0.0% |

## Schritt 4 · Muster

| Feld | Muster | Auffälligkeiten |
|---|---|---|
| `erfasst` | `DD.MM.YYYY` | konsistent |
| `email` | `xxx@xxx.xxx` | 23 fehlend |
| `tel` | `XXXX XXXXX` | 0 auffällig |
| `plz` | 5-stellig | 0 auffällig |
| `vorname` | Vollname oder Initial | 7x nur Initial (`X.`) |
| `anrede` | `Hr.` / `Fr.` | normiert |

## Schritt 5 · Auffälligkeiten

| Prüfung | Befund |
|---|---|
| Vollständig doppelte Zeilen | 0 |
| Doppelte E-Mail-Adressen | 12 |
| Vorname als Initial | 7 |
| Ungültige/fehlende E-Mail | 23 |

**Fazit:** Keine Duplikate auf Zeilenebene. Kritische Felder: `email` (fehlend) und `vorname` (Initialen), die das Matching in W9 erschwerden. Fehlende Kunden-ID erfordert alternatives Matching über Name + PLZ.
