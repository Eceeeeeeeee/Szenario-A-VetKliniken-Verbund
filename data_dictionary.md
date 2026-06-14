# Data Dictionary

Erstellt am: 2026-06-14

## Quellen x Spalten zusammengeführt

| Quelle                 | Spalte             | Datentyp       | Beispielwert         |   Anzahl Werte |   Fehlwerte |   Fehlwerte % |   Eindeutige Werte |
|:-----------------------|:-------------------|:---------------|:---------------------|---------------:|------------:|--------------:|-------------------:|
| Juckstadt Kunden       | kunden_nr          | object         | 1                    |            223 |           0 |          0    |                223 |
| Juckstadt Kunden       | anrede             | object         | Herr                 |            223 |           0 |          0    |                  2 |
| Juckstadt Kunden       | vorname            | object         | Thomas               |            223 |           0 |          0    |                 63 |
| Juckstadt Kunden       | nachname           | object         | Berger               |            223 |           0 |          0    |                 43 |
| Juckstadt Kunden       | strasse            | object         | Hauptstr. 12         |            223 |           0 |          0    |                214 |
| Juckstadt Kunden       | plz                | object         | 35500                |            223 |           0 |          0    |                  8 |
| Juckstadt Kunden       | ort                | object         | Juckstadt            |            223 |           0 |          0    |                 10 |
| Juckstadt Kunden       | telefon            | object         | 06450-1234           |            223 |           0 |          0    |                222 |
| Juckstadt Kunden       | email              | object         | berger@email.de      |            202 |          21 |          9.42 |                196 |
| Juckstadt Kunden       | angelegt_am        | object         | 2021-05-12           |            223 |           0 |          0    |                215 |
| Juckstadt Behandlungen | beh_nr             | object         | 1                    |            150 |           0 |          0    |                150 |
| Juckstadt Behandlungen | datum              | object         | 2026-02-06           |            150 |           0 |          0    |                114 |
| Juckstadt Behandlungen | patient_name       | object         | Pumba                |            150 |           0 |          0    |                 32 |
| Juckstadt Behandlungen | kunde_nachname     | object         | Krueger              |            150 |           0 |          0    |                 38 |
| Juckstadt Behandlungen | diagnose           | object         | Augenuntersuchung    |            150 |           0 |          0    |                 19 |
| Juckstadt Behandlungen | kosten_euro        | object         | 191,17               |            150 |           0 |          0    |                150 |
| Waldrand Kunden        | customer_id        | object         | W-1001               |            227 |           0 |          0    |                227 |
| Waldrand Kunden        | first_name         | object         | Thomas               |            227 |           0 |          0    |                 64 |
| Waldrand Kunden        | last_name          | object         | Berger               |            226 |           1 |          0.44 |                 47 |
| Waldrand Kunden        | street             | object         | Hauptstr. 12         |            227 |           0 |          0    |                216 |
| Waldrand Kunden        | zip_code           | object         | 35500                |            227 |           0 |          0    |                  8 |
| Waldrand Kunden        | city               | object         | Juckstadt            |            227 |           0 |          0    |                 11 |
| Waldrand Kunden        | phone              | object         | +49 645 01234        |            227 |           0 |          0    |                227 |
| Waldrand Kunden        | email_address      | object         | berger@email.de      |            177 |          50 |         22.03 |                175 |
| Waldrand Kunden        | created_at         | object         | 02/09/2022           |            227 |           0 |          0    |                212 |
| Waldrand Kunden        | marketing_consent  | object         | yes                  |            152 |          75 |         33.04 |                  2 |
| Waldrand Kunden        | created_at_dt      | datetime64[ns] | 2022-02-09           |            222 |           5 |          2.2  |                211 |
| Waldrand Behandlungen  | treatment_id       | object         | T20250151            |            150 |           0 |          0    |                150 |
| Waldrand Behandlungen  | customer_id        | object         | W-1067               |            150 |           0 |          0    |                108 |
| Waldrand Behandlungen  | animal_name        | object         | Smokey               |            150 |           0 |          0    |                 32 |
| Waldrand Behandlungen  | species            | object         | cat                  |            150 |           0 |          0    |                  2 |
| Waldrand Behandlungen  | treatment_date     | object         | 12/11/2025           |            150 |           0 |          0    |                116 |
| Waldrand Behandlungen  | diagnosis          | object         | Flea treatment       |            150 |           0 |          0    |                 19 |
| Waldrand Behandlungen  | total_eur          | object         | 199.85               |            150 |           0 |          0    |                150 |
| Waldrand Behandlungen  | total_eur_num      | float64        | 199.85               |            150 |           0 |          0    |                150 |
| Waldrand Behandlungen  | treatment_date_dt  | datetime64[ns] | 2025-12-11           |            150 |           0 |          0    |                116 |
| Schmidt Kunden         | nachname           | object         | Berger               |            234 |           0 |          0    |                 45 |
| Schmidt Kunden         | vorname            | object         | Th.                  |            234 |           0 |          0    |                 68 |
| Schmidt Kunden         | anrede             | object         | Hr.                  |            234 |           0 |          0    |                  2 |
| Schmidt Kunden         | plz                | object         | 35500                |            234 |           0 |          0    |                  8 |
| Schmidt Kunden         | ort                | object         | Juckstadt            |            234 |           0 |          0    |                 11 |
| Schmidt Kunden         | strasse            | object         | Hauptstr. 12         |            234 |           0 |          0    |                225 |
| Schmidt Kunden         | tel                | object         | 0645 01234           |            234 |           0 |          0    |                232 |
| Schmidt Kunden         | email              | object         | berger@email.de      |            211 |          23 |          9.83 |                205 |
| Schmidt Kunden         | erfasst            | object         | 06.12.2020           |            234 |           0 |          0    |                224 |
| Schmidt Kunden         | erfasst_year       | int32          | 2020                 |            234 |           0 |          0    |                  9 |
| Schmidt Behandlungen   | id                 | int64          | 301                  |            150 |           0 |          0    |                150 |
| Schmidt Behandlungen   | datum              | object         | 24.09.2025           |            150 |           0 |          0    |                108 |
| Schmidt Behandlungen   | kunde              | object         | Schneider X.         |            150 |           0 |          0    |                104 |
| Schmidt Behandlungen   | leistung           | object         | Vorsorgeuntersuchung |            150 |           0 |          0    |                 19 |
| Schmidt Behandlungen   | betrag             | object         | 15,46 EUR            |            150 |           0 |          0    |                148 |
| Schmidt Behandlungen   | tier.name          | object         | Caesar               |            150 |           0 |          0    |                 32 |
| Schmidt Behandlungen   | tier.art           | object         | Katze                |            150 |           0 |          0    |                  2 |
| Schmidt Behandlungen   | betrag_num         | float64        | 15.46                |            150 |           0 |          0    |                148 |
| Schmidt Behandlungen   | datum_dt           | datetime64[ns] | 2025-09-24           |            150 |           0 |          0    |                108 |
| Bergblick Patienten    | xml_position       | int64          | 1                    |            232 |           0 |          0    |                232 |
| Bergblick Patienten    | patient_id         | object         | P-4001               |            232 |           0 |          0    |                232 |
| Bergblick Patienten    | patient_quell_id   | object         | P-4001               |            232 |           0 |          0    |                232 |
| Bergblick Patienten    | halter_id          | object         | P-4001               |            232 |           0 |          0    |                232 |
| Bergblick Patienten    | halter_anrede      | object         | Herr                 |            232 |           0 |          0    |                  2 |
| Bergblick Patienten    | halter_name        | object         | Thomas Berger        |            232 |           0 |          0    |                222 |
| Bergblick Patienten    | halter_vorname     | object         | Thomas               |            232 |           0 |          0    |                 66 |
| Bergblick Patienten    | halter_nachname    | object         | Berger               |            232 |           0 |          0    |                 44 |
| Bergblick Patienten    | halter_telefon     | object         | 0645-01234           |            215 |          17 |          7.33 |                214 |
| Bergblick Patienten    | halter_telefon_typ | object         | festnetz             |            215 |          17 |          7.33 |                  3 |
| Bergblick Patienten    | halter_email       | object         | berger@email.de      |            210 |          22 |          9.48 |                205 |
| Bergblick Patienten    | halter_strasse     | object         | Hauptstrasse 12      |            232 |           0 |          0    |                228 |
| Bergblick Patienten    | halter_plz         | object         | 35500                |            232 |           0 |          0    |                  8 |
| Bergblick Patienten    | halter_ort         | object         | Juckstadt            |            232 |           0 |          0    |                 11 |
| Bergblick Patienten    | tier_id            | object         |                      |              0 |         232 |        100    |                  0 |
| Bergblick Patienten    | tier_name          | object         | Lucky                |            232 |           0 |          0    |                 32 |
| Bergblick Patienten    | tier_art           | object         | Hund                 |            232 |           0 |          0    |                  2 |
| Bergblick Patienten    | tier_geburt        | object         | 2022-05-03           |            232 |           0 |          0    |                222 |
| Bergblick Behandlungen | xml_position       | int64          | 1                    |            150 |           0 |          0    |                150 |
| Bergblick Behandlungen | behandlung_id      | object         |                      |              0 |         150 |        100    |                  0 |
| Bergblick Behandlungen | patient_id         | object         | P-4191               |            150 |           0 |          0    |                115 |
| Bergblick Behandlungen | datum              | object         | 2025-11-15           |            150 |           0 |          0    |                111 |
| Bergblick Behandlungen | diagnose           | object         | Tumorabklaerung      |            150 |           0 |          0    |                 19 |
| Bergblick Behandlungen | leistung           | object         |                      |              0 |         150 |        100    |                  0 |
| Bergblick Behandlungen | kosten_netto       | object         | 162.92               |            150 |           0 |          0    |                150 |
| Bergblick Behandlungen | kosten_brutto      | object         | 193.87               |            150 |           0 |          0    |                150 |
| Bergblick Behandlungen | kosten_netto_num   | float64        | 162.92               |            150 |           0 |          0    |                150 |
| Bergblick Behandlungen | kosten_brutto_num  | float64        | 193.87               |            150 |           0 |          0    |                150 |
| Bergblick Behandlungen | steuer_faktor      | float64        | 1.1899705376872085   |            150 |           0 |          0    |                149 |
