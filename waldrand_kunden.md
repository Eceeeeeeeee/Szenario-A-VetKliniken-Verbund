# Profiling-Report: praxis_waldrand_kunden.csv

_Erstellt: 2026-06-07_

## Schritt 1 · Struktur

| Merkmal | Wert |
|---|---|
| Format | CSV |
| Encoding | UTF-8 |
| Trennzeichen | Komma `,` |
| Header | ja |
| Zeilen | 227 |
| Spalten | 11 |
| Spaltennamen | customer_id, first_name, last_name, street, zip_code, city, phone, email_address, created_at, marketing_consent, created_at_dt |

**Beobachtung:** Die Kundendatei liegt als CSV-Datei mit UTF-8-Encoding vor und enthält 227 Kundendatensätze.

## Schritt 2 · Wertebereiche

| Feld | Distinct Values | Fehlwerte |
|---|---:|---:|
| customer_id | 227 | 0 |
| first_name | 64 | 0 |
| last_name | 47 | 1 |
| street | 216 | 0 |
| zip_code | 8 | 0 |
| city | 11 | 0 |
| phone | 227 | 0 |
| email_address | 175 | 50 |
| created_at | 212 | 0 |
| marketing_consent | 2 | 75 |

**Top-3 Städte:**

city
Rabenau      73
Allendorf    69
Londorf      55

**Beobachtung:** Die Kunden verteilen sich auf mehrere Städte, wobei Rabenau, Allendorf und Londorf besonders häufig vorkommen.

## Schritt 3 · Fehlwerte

| Feld | Fehlwerte |
|---|---:|
| email_address | 50 |
| marketing_consent | 75 |
| last_name | 1 |

**Beobachtung:** Die größten Datenqualitätsprobleme betreffen die Felder `marketing_consent` und `email_address`.

## Schritt 4 · Muster

| Feld | Muster | Auffälligkeiten |
|---|---|---|
| created_at | MM/DD/YYYY | 5 Werte nicht parsebar |
| phone | verschiedene Schreibweisen | uneinheitliche Telefonnummernformate |
| marketing_consent | yes / no / fehlend | 75 fehlende Werte |
| email_address | E-Mail-Adresse | 50 fehlende Werte |

**Beobachtung:** Telefonnummern liegen in unterschiedlichen Formaten vor. Außerdem konnten 5 Werte im Feld `created_at` nicht als gültiges Datum interpretiert werden.

## Schritt 5 · Auffälligkeiten

| Prüfung | Befund |
|---|---:|
| Doppelte customer_id | 0 |
| Doppelte E-Mail-Adressen | 2 |
| Ungültige created_at-Werte | 5 |
| Fehlende E-Mail-Adressen | 50 |
| Fehlende Marketing-Einwilligungen | 75 |

**Fazit:** Die Kundendatei ist strukturell gut nutzbar, weist aber mehrere Datenqualitätsprobleme auf. Besonders relevant sind fehlende E-Mail-Adressen, fehlende Marketing-Einwilligungen, uneinheitliche Telefonnummernformate und ungültige Datumswerte im Feld `created_at`.
