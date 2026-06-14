# Fehlerliste

Erstellt am: 2026-06-14

## Datenqualitätsprobleme

Die Fehlerliste enthält konkret benannte Datenqualitätsprobleme über alle analysierten Praxen.

Kategorien:
Schema-Drift, Format, Encoding, Fehlwerte, Dubletten, Semantik

| Praxis      | Quelle                            | Kategorie    | Feld                                   | Problem                                                      | Begründung                                                                                    | Priorität   |
|:------------|:----------------------------------|:-------------|:---------------------------------------|:-------------------------------------------------------------|:----------------------------------------------------------------------------------------------|:------------|
| Juckstadt   | praxis_juckstadt_kunden.csv       | Fehlwerte    | email / telefon                        | Kontaktinformationen teilweise leer                          | Fehlende Kontaktfelder erschweren Kundenkommunikation und Dublettenprüfung.                   | Mittel      |
| Juckstadt   | praxis_juckstadt_kunden.csv       | Format       | plz                                    | Postleitzahlen müssen als String behandelt werden            | PLZ darf nicht numerisch verarbeitet werden, da führende Nullen verloren gehen können.        | Hoch        |
| Juckstadt   | praxis_juckstadt_behandlungen.csv | Semantik     | kosten_euro                            | Betrag ist fachlich Brutto/Netto nicht eindeutig             | Ohne klare Semantik ist die spätere Abrechnungsauswertung unsicher.                           | Hoch        |
| Waldrand    | praxis_waldrand.json              | Schema-Drift | customer_id / treatment_id             | Andere Feldnamen als in Juckstadt                            | Gleiche fachliche Konzepte werden mit anderen Spaltennamen geliefert.                         | Hoch        |
| Waldrand    | praxis_waldrand.json              | Format       | JSON-Struktur                          | Verschachtelte Struktur muss geflattet werden                | Für ein gemeinsames Zielmodell müssen verschachtelte Objekte in Tabellenform gebracht werden. | Hoch        |
| Waldrand    | praxis_waldrand.json              | Semantik     | total_eur                              | Betrag ist nicht eindeutig als Netto oder Brutto beschrieben | Die Bedeutung des Betrags muss vor der Integration geklärt werden.                            | Mittel      |
| Schmidt     | praxis_schmidt.xml                | Schema-Drift | kunden_id                              | Keine stabile Kunden-ID vorhanden                            | Kunden können nicht zuverlässig über eine technische ID zusammengeführt werden.               | Hoch        |
| Schmidt     | praxis_schmidt.xml                | Format       | XML-Struktur                           | XML muss vor Analyse und Mapping normalisiert werden         | Die Daten liegen nicht direkt tabellarisch vor.                                               | Hoch        |
| Schmidt     | praxis_schmidt.xml                | Encoding     | Textfelder                             | Sonderzeichen und Umlaute müssen geprüft werden              | Bei XML-Importen können Encoding-Probleme in Namen, Diagnosen oder Ortsangaben auftreten.     | Mittel      |
| Bergblick   | praxis_bergblick.csv              | Dubletten    | halter_id / tier_name / datum          | Mögliche Mehrfacherfassungen gleicher Behandlungen           | Kombinationen aus Halter, Tier und Datum sollten auf Dubletten geprüft werden.                | Hoch        |
| Bergblick   | praxis_bergblick.csv              | Schema-Drift | kosten_netto / kosten_brutto           | Bergblick trennt Netto und Brutto, andere Praxen nicht       | Das Zielmodell muss Betragsfelder vereinheitlichen.                                           | Hoch        |
| Alle Praxen | alle Quellen                      | Semantik     | tier_name / patient_name / animal_name | Tiername ist keine eindeutige Tier-ID                        | Mehrere Tiere können gleich heißen; Tiernamen dürfen nicht als Schlüssel verwendet werden.    | Hoch        |
