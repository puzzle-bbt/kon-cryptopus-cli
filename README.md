# 1.1 Aufgabenstellung

## 1.1.1 Titel der Arbeit

Cryptopus Command Line Client - ccli

## 1.1.2 Thematik

Implementieren eines Command Line Clients für Cryptopus welcher via JSON-API über die benutzerspezifischen API-User auf Accountdaten und Files zugreifen kann. Ergänzend dazu soll es möglich sein direkt k8s/Openshift Secrets zu Pullen / Pushen.

## 1.1.3 Ausgangslage

Cryptopus hat heute bereits ein JSON Api welches zurzeit hauptsächlich vom Frontend (EmberJS) konsumiert wird. 

https://github.com/puzzle/cryptopus/wiki/API 

## 1.1.5 Funktionale Anforderungen

### Stufe Basic

* Login als API User - ccli login https://cryptopus.example.com --token=das9asdfjyxc9desf8isdf34dasdsfadfs
  * Token beinhaltet API Usernamen sowie den aktuell gültigen Token (Base64)
  * Gewählter API User und Token werden im Homedir des Users gespeichert z.B.: ~/.ccli/session
  * Loginbefehl kann im UI von Cryptopus bei den API Usern mit einer Copy-Funktion kopiert werden (Analog Openshift), der Token wird automatisch renewed bei Zugriff auf die Copy-Funktion
* Ausloggen / Löschen session Datei - ccli logout
* Auf einen Account per account id zugreifen - ccli account 42
  * Gibt standardmässig den Account mit allen Attrs zurück (Yaml format)
  * --password flag gibt nur das Passwort als String zurück
  * --username dito für Username
* Wechseln auf aktuellen Folder mit id - ccli folder 813
  * Ausgewählter Folder wird gemerkt (in .ccli/session)
* Secret aus Openshift holen und im aktuellen Folder erstellen/updaten - ccli ose secret pull [$secret-name]
  * Es muss zuvor ein Folder gewählt werden
  * Berücksichtigt nur das aktuell ausgewählte Openshift Projekt
  * oc client muss installiert sein, Projekt muss ausgewählt sein
  * wird der Param $secret-name nicht mitgegeben, werden sämtliche Secrets abgeholt
  * Bereits existierende Einträge werden überschrieben
  * Name des Account::OpenshiftSecret = openshift secret name
* Secret aus dem aktuell ausgewählten Ordner lesen und im gewählten Openshift Projekt erstellen/update - ccli ose secret push [$secret-name]
* ccli mit --help oder ohne Argumente printed eine Hilfe
* README.md mit Anleitung in Englisch

### Stufe Comfort

Falls genügend Zeit vorhanden, folgende weiter Features umsetzen:

* Update Funktionalität für Accounts
* Login - ccli login https://cryptopus.example.com
  * Beim ersten Login wird eine Liste aller API-Users angezeigt. Der User wählt dann aus welchen API User er gerne verwenden möchte (falls nur 1, diesen gleich auswählen)
  * Der Token des gewählten API Users wird renewed falls dieser nicht mehr gültig ist
  * Wurde bereits zuvor ein API User gewählt, wird geprüft ob der Token immer noch gültig ist, falls nicht wird dieser erneuert
  * Info mit welchem API User das erfolgreich/nicht erfolgreich angemeldet wurde
  * Auth User Human per Keycloak wenn Keycloak aktiv
* Auflisten aller API Users - ccli api-users
* Auswählen eines anderen API Users - ccli api-user 42 (id oder alternativ auch namen bob-adfd42)
* Falls bei einem der Actions die Auth per API User failed, den API Token renewen (benötigt Benutzer/Passwort des Human Users)

## 1.1.6 Nicht funktionale Anforderungen

* Im Backend Account neu als STI, Neuer Account Typ Account::OpenshiftSecret, verschlüsseltes data Attribut, Daten als Base64 ablegen
  * Secret im UI nur anzeigen, kann nicht via UI editiert werden
* Source Code https://github.com/puzzle/ccli
* ccli kann einfach als einzelnes File auf ein System kopiert werden (installation z.B. mit wget)
* rspec Tests sowie Travis build
* Muss mit Standard System Ruby lauffähig sein (Aktuelle Ubuntu Ausgabe, Ubuntu Setup Puzzle)

## 1.1.7 Aufgabenstellung

### Konzeption

Grobe Konzeption für Stufe Basic mit Vorausblick auf Stufe Comfort

1. Use Cases dokumentieren
1. Grobe Terminplanung
1. Architektur konzipieren (Flussdiagramme, Klassendiagramme, usw.)
1. Anforderungen Openshift Secret (Datentyp, Länge, Encoding, weitere Attribute, usw.)

Alle Konzeption Dokumente in diesem Repo unter doc ablegen. Beispiel: https://github.com/puzzle/mailbox-watcher/tree/master/doc

### Umsetzung

Hier ein Vorschlag für die technische Umsetzung: (kann während der Konzeption noch angepasst werden)

1. Setup rspec, Travis build
1. Gem für Command Line evaluieren. z.B. https://rubygems.org/gems/commander
1. --help für Stufe Basic implementieren
1. Login/Logout implementieren
1. Backend: STI Account, Account::OpenshiftSecret, data attribute
1. Read Account Feature
1. Select Folder Feature
1. Pull / Push Openshift Secret
1. Comfort Features

## 1.1.8 Mittel / Methoden / Projektmethode
 
Wir werden folgende Technologien brauchen:

* Ruby
* Rubygems
* Ruby on Rails
* Ein Bischen Ember
* Openshift
* YAML
