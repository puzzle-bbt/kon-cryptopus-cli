# Use Case 2: Secret aus Openshift in Cryptopus abspeichern

## 2.1

| Bezeichnung         | Ein Benutzer möchte ein Openshift Secret im Cryptopus Ordner mit id **1** speichern                                                                                                                                           |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Vorbedingungen      | <ul><li> Eine Cryptopus Instanz mit einem Ordner mit id **1** läuft auf https://cryptopus.example.com</li><li>Mit `oc` muss ein vorhandenes Openshift Projekt mit einem Secret namens `credentials` ausgewählt sein</li></ul> |
| Akteure             | <ul><li>Benutzer</li><li>Openshift</li><li>Cryptopus</li></ul>                                                                                                                                                                |
| Auslöser            | Der Benutzer möchte sein Secret aus Openshift auf in Cryptopus speichern                                                                                                                                                      |
| Ablauf              | <ol><li>`ccli login https://cryptopus.example.com --token=safeLoginToken`</li><li>`ccli folder 1`</li><li>`ccli ose secret pull credentials`</li></ol>                                                                        |
| Erwartetes Ergebnis | In Cryptopus wird ein neuer Account mit dem Accountnamen `credentials` angelegt. Dieser enthält als Passwort die Secret Daten in Base64 encoded.                                                                              |
| Mögliche Fehler     | <ul><li>Token hat nicht die benötigte Berechtigung (403)</li><li>Ordner wurde nicht gefunden (404)</li><li>Secret mit Namen `credentials` wurde nicht gefunden (404)</li></ul>                                                |

## 2.2

| Bezeichnung         | Ein Benutzer möchte alle Openshift Secrets im Cryptopus Ordner mit id **1** speichern                                                                                                                           |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Vorbedingungen      | <ul><li> Eine Cryptopus Instanz mit einem Ordner mit id **1** läuft auf https://cryptopus.example.com</li><li>Mit `oc` muss ein vorhandenes Openshift Projekt mit angewählten Secrets ausgewählt sein</li></ul> |
| Akteure             | <ul><li>Benutzer</li><li>Openshift</li><li>Cryptopus</li></ul>                                                                                                                                                  |
| Auslöser            | Der Benutzer möchte seins Secrets aus Openshift auf in Cryptopus speichern                                                                                                                                      |
| Ablauf              | <ol><li>`ccli login https://cryptopus.example.com --token=safeLoginToken`</li><li>`ccli folder 1`</li><li>`ccli ose secret pull`</li></ol>                                                                      |
| Erwartetes Ergebnis | In Cryptopus wird für jedes Secret ein neuer Account mit dem Secret Namen angelegt. Dieser enthält als Passwort die Secret Daten in Base64 encoded.                                                             |
| Mögliche Fehler     | <ul><li>Token hat nicht die benötigte Berechtigung (403)</li><li>Ordner wurde nicht gefunden (404)</li></ul>                                                                                                    |

## 2.3

| Bezeichnung         | Ein Benutzer möchte ein Openshift Secret im Cryptopus Ordner mit id **1** synchronisieren                                                                                                                                                                                                                                                     |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Vorbedingungen      | <ul><li> Eine Cryptopus Instanz mit einem Ordner mit id **1** läuft auf https://cryptopus.example.com</li><li>Mit `oc` muss ein vorhandenes Openshift Projekt mit einem Secret namens `credentials` ausgewählt sein</li><li>Im Cryptopus Ordner mit id **1** muss ein Secrets Account mit dem Accountnamen `credentials` existieren</li></ul> |
| Akteure             | <ul><li>Benutzer</li><li>Openshift</li><li>Cryptopus</li></ul>                                                                                                                                                                                                                                                                                |
| Auslöser            | Der Benutzer möchte sein Secret aus Openshift auf in Cryptopus synchronisieren                                                                                                                                                                                                                                                                |
| Ablauf              | <ol><li>`ccli login https://cryptopus.example.com --token=safeLoginToken`</li><li>`ccli folder 1`</li><li>`ccli ose secret pull credentials`</li></ol>                                                                                                                                                                                        |
| Erwartetes Ergebnis | In Cryptopus wird der bereits vorhandene Account mit dem Accountnamen `credentials` überschrieben. Dieser enthält als Passwort die aktuellen Secret Daten in Base64 encoded.                                                                                                                                                                  |
| Mögliche Fehler     | <ul><li>Token hat nicht die benötigte Berechtigung (403)</li><li>Ordner wurde nicht gefunden (404)</li><li>Secret mit Namen `credentials` wurde nicht gefunden (404)</li></ul>                                                                                                                                                                |