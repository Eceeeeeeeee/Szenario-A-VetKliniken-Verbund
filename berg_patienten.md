# Profiling: praxis_bergblick_export.xml – Patienten/Halter/Tiere

_Erstellt: 2026-06-14_

## Datei
- Format: XML
- Namespace: `http://vetkliniken-hessen.de/schema/v2`
- Encoding: UTF-8
- Header: nein, XML-Struktur
- Zeilen Patienten/Halter/Tiere: 232
- Spalten nach Flattening: 18

## Fachliche Einordnung
Die Bergblick-Quelle unterscheidet sich deutlich von den CSV- und JSON-Quellen, da Halter- und Tierinformationen gemeinsam in verschachtelten XML-Elementen gespeichert sind. Für die weitere Verarbeitung müssen diese Informationen zuerst in eine tabellarische Form überführt werden.

## Spalten

| Spalte             | Typ-Vermutung   | Beispiel        |   Distinct | Null%   | Bemerkung   |
|:-------------------|:----------------|:----------------|-----------:|:--------|:------------|
| xml_position       | NUMERIC         | 1               |        232 | 0.0%    |             |
| patient_id         | VARCHAR         | P-4001          |        232 | 0.0%    |             |
| patient_quell_id   | VARCHAR         | P-4001          |        232 | 0.0%    |             |
| halter_id          | VARCHAR         | P-4001          |        232 | 0.0%    |             |
| halter_anrede      | VARCHAR         | Herr            |          2 | 0.0%    |             |
| halter_name        | VARCHAR         | Thomas Berger   |        222 | 0.0%    |             |
| halter_vorname     | VARCHAR         | Thomas          |         66 | 0.0%    |             |
| halter_nachname    | VARCHAR         | Berger          |         44 | 0.0%    |             |
| halter_telefon     | VARCHAR         | 0645-01234      |        214 | 7.3%    |             |
| halter_telefon_typ | VARCHAR         | festnetz        |          3 | 7.3%    |             |
| halter_email       | VARCHAR         | berger@email.de |        205 | 9.5%    |             |
| halter_strasse     | VARCHAR         | Hauptstrasse 12 |        228 | 0.0%    |             |
| halter_plz         | NUMERIC         | 35500           |          8 | 0.0%    |             |
| halter_ort         | VARCHAR         | Juckstadt       |         11 | 0.0%    |             |
| tier_id            | VARCHAR         | –               |          0 | 100.0%  |             |
| tier_name          | VARCHAR         | Lucky           |         32 | 0.0%    |             |
| tier_art           | VARCHAR         | Hund            |          2 | 0.0%    |             |
| tier_geburt        | DATE            | 2022-05-03      |        222 | 0.0%    |             |

## Ergebnisinterpretation
Das Profiling zeigt, dass die wesentlichen fachlichen Informationen für Halter und Tiere vorhanden sind. Patient-ID, Name, Adresse, Tiername, Tierart und Tiergeburtsdatum sind vollständig. Auffällig sind fehlende Kontaktinformationen: Telefonnummern fehlen bei 17 Datensätzen und E-Mail-Adressen bei 22 Datensätzen. Das ist besonders relevant für das spätere Matching, da Telefon und E-Mail starke Identifikatoren für Dublettenerkennung sind.

## Auffällige Muster
- XML-Datei verwendet einen Namespace; XPath-Abfragen müssen den Namespace berücksichtigen.
- Halter- und Tierdaten liegen verschachtelt innerhalb eines `patient`-Elements.
- Kontakt- und Adressdaten liegen in Unterelementen wie `kontakt` und `adresse`.
- Für Staging und Transform ist ein explizites Flattening notwendig.
- Die Patient-ID ist das zentrale Referenzmerkmal für spätere Behandlungen.
- Eine separate Tier-ID ist nicht vorhanden; Tierinformationen müssen über Patient-ID und Tierattribute zugeordnet werden.

## Tierarten

| tier_art   |   anzahl |
|:-----------|---------:|
| Katze      |      121 |
| Hund       |      111 |

## Datenqualitätsprobleme

| kategorie       | quelle         | feld            |   anzahl | beschreibung                                                                                                                        |
|:----------------|:---------------|:----------------|---------:|:------------------------------------------------------------------------------------------------------------------------------------|
| Schema/Struktur | berg_patienten | XML             |        1 | Bergblick ist keine flache Datei, sondern eine XML-Datei mit verschachtelten Patient-, Halter- und Tierdaten.                       |
| Encoding/Parser | berg_export    | Namespace       |        1 | XML verwendet einen Namespace; Parser/XPath-Abfragen müssen namespace-aware umgesetzt werden.                                       |
| Fehlwerte       | berg_patienten | patient_id      |        0 | Patient-ID fehlt; dadurch wären Provenance und Referenzierung von Behandlungen gefährdet.                                           |
| Dubletten       | berg_patienten | patient_id      |        0 | Patient-ID kommt mehrfach vor; das wäre für eindeutige Referenzierung auffällig.                                                    |
| Fehlwerte       | berg_patienten | halter_vorname  |        0 | Vorname fehlt; dieses Feld ist für Matching, Normalisierung oder fachliche Auswertung relevant.                                     |
| Fehlwerte       | berg_patienten | halter_nachname |        0 | Nachname fehlt; dieses Feld ist für Matching, Normalisierung oder fachliche Auswertung relevant.                                    |
| Fehlwerte       | berg_patienten | halter_telefon  |       17 | Telefonnummer fehlt; dieses Feld ist für Matching, Normalisierung oder fachliche Auswertung relevant.                               |
| Fehlwerte       | berg_patienten | halter_email    |       22 | E-Mail fehlt; dieses Feld ist für Matching, Normalisierung oder fachliche Auswertung relevant.                                      |
| Fehlwerte       | berg_patienten | halter_strasse  |        0 | Straße fehlt; dieses Feld ist für Matching, Normalisierung oder fachliche Auswertung relevant.                                      |
| Fehlwerte       | berg_patienten | halter_plz      |        0 | PLZ fehlt; dieses Feld ist für Matching, Normalisierung oder fachliche Auswertung relevant.                                         |
| Fehlwerte       | berg_patienten | halter_ort      |        0 | Ort fehlt; dieses Feld ist für Matching, Normalisierung oder fachliche Auswertung relevant.                                         |
| Fehlwerte       | berg_patienten | tier_name       |        0 | Tiername fehlt; dieses Feld ist für Matching, Normalisierung oder fachliche Auswertung relevant.                                    |
| Fehlwerte       | berg_patienten | tier_art        |        0 | Tierart fehlt; dieses Feld ist für Matching, Normalisierung oder fachliche Auswertung relevant.                                     |
| Schema/Struktur | berg_patienten | tier_id         |      232 | Die Quelle liefert keine separate Tier-ID; für die Pipeline muss die Zuordnung über patient_id, tier_name und tier_geburt erfolgen. |
| Format          | berg_patienten | halter_email    |        0 | E-Mail entspricht nicht dem erwarteten Grundmuster name@domain.tld.                                                                 |
| Format          | berg_patienten | halter_telefon  |        0 | Telefonnummer weicht vom erwarteten deutschen Format mit führender 0 oder +49 ab.                                                   |

## Bewertung für die Pipeline
Die Quelle ist fachlich gut nutzbar, erfordert aber einen XML-spezifischen Parser. Besonders wichtig sind Namespace-Handling, Flattening der Halter-/Tierstruktur und der Erhalt der Patient-ID als Provenance- und Referenzmerkmal. Fehlende Kontaktinformationen müssen später im Matching berücksichtigt werden, weil dadurch E-Mail- oder Telefon-Matches nicht für alle Datensätze möglich sind.
