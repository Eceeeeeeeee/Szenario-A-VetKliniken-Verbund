# Profiling-Report: praxis_schmidt_behandlungen.json

_Erstellt: 2026-06-07_

## Schritt 1 · Struktur

| Merkmal | Wert |
|---|---|
| Format | JSON (Array of Objects) |
| Encoding | UTF-8 |
| Header | nein (JSON-Keys) |
| Einträge (roh) | 150 |
| Spalten nach Flatten | 7 |
| Verschachtelung | `tier` → `tier.name`, `tier.art` |

## Schritt 2 · Wertebereiche

| Spalte | Typ-Vermutung | Beispiel | Distinct | Null% | Bemerkung |
|---|---|---|---:|---:|---|
| `id` | INTEGER | 301 | 150 | 0.0% |  |
| `datum` | DATE | 24.09.2025 | 108 | 0.0% |  |
| `kunde` | VARCHAR | Schneider X. | 104 | 0.0% |  |
| `leistung` | VARCHAR | Vorsorgeuntersuchung | 19 | 0.0% |  |
| `betrag` | VARCHAR | 15,46 EUR | 148 | 0.0% |  |
| `tier.name` | VARCHAR | Caesar | 32 | 0.0% |  |
| `tier.art` | VARCHAR | Katze | 2 | 0.0% |  |

**Betrag (geparst):** Min 15.46 EUR – Max 199.50 EUR – Mean 100.64 EUR
**Datum:** 2025-09-01 bis 2026-04-04

## Schritt 3 · Fehlwerte

Keine fehlenden Werte. Alle 150 Datensätze sind vollständig.

## Schritt 4 · Muster

| Feld | Muster | Auffälligkeiten |
|---|---|---|
| `datum` | `DD.MM.YYYY` | konsistent, 0 nicht parsebar |
| `betrag` | `XX,XX EUR` | Komma-Dezimaltrenner; 0 auffällig |
| `kunde` | `Nachname X.` | Initiale statt Vorname; erschwertes Matching |
| `tier.art` | `Katze` / `Hund` | normiert, nur 2 Ausprägungen |

## Schritt 5 · Auffälligkeiten

| Prüfung | Befund |
|---|---|
| Vollständig doppelte Zeilen | 0 |
| Doppelte Behandlungs-ID | 0 |
| Betrags-Ausreißer (IQR) | 0 |
| Behandlungen ohne Kunden-Match | 0 |

**Fazit:** Die Behandlungsdatei ist vollständig und konsistent. Kritische Punkte: (1) `betrag` als String muss geparst werden, (2) `tier` muss vor Staging geflattet werden, (3) Kunden-Matching erfordert name-basierte Normalisierung, da keine gemeinsame ID vorhanden ist.
