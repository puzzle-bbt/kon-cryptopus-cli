# Use Cases

## Akteure

| Name      | Beschreibung                                                                                                                                                                                                                               |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Benutzer  | Der Benutzer ist meist ein Entwickler und muss die Secrets seiner Openshift Projekte verwalten. Als Passwortmanager nutzt er Cryptopus.                                                                                                    |
| Openshift | Als Schnittstelle zu Openshift wird das CLI Tool `oc` verwendet. Openshift verwaltet mehrere Projekte welche verschiedene Secrets enthalten.                                                                                               |
| Cryptopus | Cryptopus ist ein Passwortmanager in dem Accounts gespeichert werden können. Diese werden innerhalb von Ordnern verwaltet. Zur Kommunikation mit Cryptopus wird die [Cryptopus API](https://github.com/puzzle/cryptopus/wiki/API) genutzt. |

## Use Cases

| Nummer | Bezeichnung                                                                                                                                         |
| ------ | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1      | [Accountdaten abfragen](https://github.com/puzzle/ccli/blob/master/docs/use_cases/1_use_cases.md)                                    |
| 2      | [Secret aus Openshift in Cryptopus abspeichern](https://github.com/puzzle/ccli/blob/master/docs/use_cases/2_use_cases.md)            |
| 3      | [Secret aus Cryptopus auslesen und in Openshift eintragen](https://github.com/puzzle/ccli/blob/master/docs/use_cases/3_use_cases.md) |
