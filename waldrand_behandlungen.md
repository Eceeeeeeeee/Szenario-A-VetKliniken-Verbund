# Profiling-Report: praxis_waldrand_behandlungen.csv

_Erstellt: 2026-06-07_

## Schritt 1 · Struktur

| Merkmal | Wert |
|---|---|
| Format | CSV |
| Encoding | UTF-8 |
| Trennzeichen | Komma `,` |
| Header | ja |
| Zeilen | 150 |
| Spalten | 9 |
| Spaltennamen | treatment_id, customer_id, animal_name, species, treatment_date, diagnosis, total_eur, total_eur_num, treatment_date_dt |

**Beobachtung:** Die Behandlungsdatei enthält 150 Datensätze mit Informationen zu Kunde, Tier, Behandlung, Datum und Rechnungsbetrag.

## Schritt 2 · Wertebereiche

| Kennzahl | Wert |
|---|---:|
| Minimaler Rechnungsbetrag | 15.30 € |
| Maximaler Rechnungsbetrag | 199.85 € |
| Durchschnittlicher Rechnungsbetrag | 114.89 € |
| Anzahl unterschiedlicher Tierarten | 2 |
| Anzahl unterschiedlicher Diagnosen | 19 |
| Anzahl unterschiedlicher Kunden in Behandlungen | 108 |

**Tierarten:**

species
cat    76
dog    74

**Beobachtung:** Die Rechnungsbeträge bewegen sich zwischen 15.30 € und 199.85 €. Hunde und Katzen treten nahezu gleich häufig auf.

## Schritt 3 · Fehlwerte

| Prüfung | Wert |
|---|---:|
| Fehlwerte gesamt | 0 |
| Ungültige treatment_date-Werte | 0 |
| Ungültige total_eur-Werte | 0 |

**Beobachtung:** In der Behandlungsdatei treten keine relevanten Fehlwerte auf.

## Schritt 4 · Muster

| Feld | Muster | Auffälligkeiten |
|---|---|---|
| treatment_date | MM/DD/YYYY | 0 Werte nicht parsebar |
| total_eur | numerischer Betrag mit Punkt | 0 ungültige Werte |
| species | cat / dog | normierte Werte |
| diagnosis | Freitext / Leistung | mehrere unterschiedliche Diagnosen |

**Top-10 Diagnosen:**

diagnosis
Dressing change        13
Ultrasound             12
Check-up               11
X-ray                  11
Neutering               9
Eye examination         9
Dental scaling          9
Ear infection           9
Flea/tick treatment     8
Follow-up               8

**Beobachtung:** Die Datums- und Betragsformate sind weitgehend konsistent. Die häufigsten Leistungen sind Dressing Change, Ultrasound, X-ray und Check-up.

## Schritt 5 · Auffälligkeiten

| Prüfung | Befund |
|---|---:|
| Doppelte treatment_id | 0 |
| Ungültige treatment_date-Werte | 0 |
| Ungültige total_eur-Werte | 0 |

**Fazit:** Die Behandlungsdatei besitzt insgesamt eine hohe Datenqualität. Die Behandlungs-IDs sind eindeutig, Datums- und Betragswerte konnten erfolgreich verarbeitet werden, und es treten keine relevanten Fehlwerte auf. Die Rechnungsbeträge liegen in einem plausiblen Bereich zwischen ca. 15 € und 200 €.
