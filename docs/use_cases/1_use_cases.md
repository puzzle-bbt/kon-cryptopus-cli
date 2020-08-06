# Use Case 1: Accountdaten abfragen

## 1.1

| Bezeichnung         | Ein Benutzer möchte alle Daten eines Accounts abfragen                                                                                                                               |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Vorbedingungen      | <ul><li> Eine Cryptopus Instanz mit einem Account mit der id **1** läuft auf https://cryptopus.example.com</li><li>Der Benutzer hat per Api Nutzer Zugriff auf den Account</li></ul> |
| Akteure             | <ul><li>Benutzer</li><li>Cryptopus</li></ul>                                                                                                                                         |
| Auslöser            | Der Benutzer möchte auf die Daten des Accounts mit id **1** auslesen                                                                                                                 |
| Ablauf              | <ol><li>`ccli login https://cryptopus.example.com --token=safeLoginToken`</li><li>`ccli account 1`</li></ol>                                                                         |
| Erwartetes Ergebnis | Alle Accountdaten inkl entschlüsseltem Passwort im YAML Format                                                                                                                       |
| Mögliche Fehler     | <ul><li>Token hat nicht die benötigte Berechtigung (403)</li><li>Account wurde nicht gefunden (404)</li></ul>                                                                        |

## 1.2

| Bezeichnung         | Ein Benutzer möchte den Nutzernamen eines Accounts abfragen                                                                                                                          |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Vorbedingungen      | <ul><li> Eine Cryptopus Instanz mit einem Account mit der id **1** läuft auf https://cryptopus.example.com</li><li>Der Benutzer hat per Api Nutzer Zugriff auf den Account</li></ul> |
| Akteure             | <ul><li>Benutzer</li><li>Cryptopus</li></ul>                                                                                                                                         |
| Auslöser            | Der Benutzer möchte den Benutzernamen des Accounts mit id **1** auslesen                                                                                                             |
| Ablauf              | <ol><li>`ccli login https://cryptopus.example.com --token=safeLoginToken`</li><li>`ccli account --username 1`</li></ol>                                                              |
| Erwartetes Ergebnis | Den Benutzernamen des Accounts                                                                                                                                                       |
| Mögliche Fehler     | <ul><li>Token hat nicht die benötigte Berechtigung (403)</li><li>Account wurde nicht gefunden (404)</li></ul>                                                                        |

## 1.3

| Bezeichnung         | Ein Benutzer möchte das Passwort eines Accounts abfragen                                                                                                                             |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Vorbedingungen      | <ul><li> Eine Cryptopus Instanz mit einem Account mit der id **1** läuft auf https://cryptopus.example.com</li><li>Der Benutzer hat per Api Nutzer Zugriff auf den Account</li></ul> |
| Akteure             | <ul><li>Benutzer</li><li>Cryptopus</li></ul>                                                                                                                                         |
| Auslöser            | Der Benutzer möchte das Passwort des Accounts mit id **1** auslesen                                                                                                                  |
| Ablauf              | <ol><li>`ccli login https://cryptopus.example.com --token=safeLoginToken`</li><li>`ccli account --password 1`</li></ol>                                                              |
| Erwartetes Ergebnis | Das Passwort des Accounts                                                                                                                                                            |
| Mögliche Fehler     | <ul><li>Token hat nicht die benötigte Berechtigung (403)</li><li>Account wurde nicht gefunden (404)</li></ul>                                                                        |

