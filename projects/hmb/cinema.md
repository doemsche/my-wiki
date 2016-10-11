# HMB Kino

## Beschreibung / Setup
Das Kino ist eine Applikation die aus 3 Teilen besteht:
1) Kino Interface (Frontend)
2) Kino Interface (Backend)
3) Kino Projector (Projector)
Das Frontend ist für den Museums-Besucher. Dieser kann auf einem Touchscreen verschiedene Filme (aus einer Datenbank) auswählen, welche auf einer Leinwand abgespielt werden.

Das Backend ist für das Museums-Personal. Dieses kann hier gemäss Anleitung neue Filme auf einen Share kopieren und mittels CMS-Funktionalität eine Filmdatenbank verwalten. Die Datenbank ist dieselbe, wo das Frontend drauf zugreift.

Es gibt 2 Mac-Minis. Auf dem Kino Interface läuft 1)Frontend und 2)Backend, Auf 3)Projector läuft nur ein Browser im Kioskmodus, welcher über eine Websocket Kommunikation Filme abspielt. Die Filme sind aber physischa auf dem Kino Interface, wo auch die Datenbank verwaltet wird.

## Client Configuration

### Software / Hardware
Das Basis Image beinhaltet die folgend aufgelisteten Software Pakete, welche auf einem Mac Mini (late 2014) laufen. 
- Type 'production': (required) Notwendig um als Kontextualisator zu laufen
- Type 'build': (optional) zum builden der individuellen Kontextualisatoren
- Type 'support': (optional) für den Support der Stationen


| Software           | Type        | Purpose
| ------------------ | ----------- | -----------------------
| OSX 10.5.5         | production  | OS
| nodejs             | production  | ctx-server, http-light-service
| mongodb            | production  | Datenbank
| ImageMagick        | production  | Bildverarbeitung
| iCab               | production  | ctx-server UI
| UPDD Driver        | production  | Touch Screen Hardware Driver
| npm                | production  | package manager nodejs
| LaunchControl      | production  | System Startup
| cliclick           | production  | System Startup
| bower (node moduel)| build       | for building ctx-stations
| git                | support     | for updates
| iTerm              | support     | development & support
| atom.io            | support     | development & support
| oh-my-zsh          | support     | development & support
| teamviewer host    | support     | development & support
| Google Chrome      | support     | development & support
| mongoHub           | support     | db GUI

##Network Config
Spezial-Station| ID | IP-Address    |
-------------- | ---| --------------|
Kino Interface | 18 | 192.168.1.169 |
Kino Projector | 19 | 192.168.1.170 |

##Setup
Auf dem Kino Interface läuft während der Ausstellung das Frontend. Auf dem Projector läuft eine Webseite, welche auf das Kino-Interface zugreift und von dort die Filme abspielt. (@Eddi => Projector kann evt. auch Brightsign sein untested though... sorry für die späte Erkenntnis).

Aufgaben:
-Projector: Abspielen von Film und Ton
-Interface: Hosting von Filmen, Frontend und Backend

Die Routes (URI's) um die verschiedenen Seiten darzustellen lauten wie folgt:
-Projector: http://localhost:5000/cinema
-Frontend (Ausstellung): http://localhost:5000/frontend
-Backend (Admin): http://localhost:5000/backend

##LaunchControl
Das Kino Interface wird über einen Service per launchctl gestartet. Der Status des Service ist über das Trayicon abrufbar.
Kino Projector läuft im Presentation-Modus von Google Chrome, da iCab eine grössere Socket-Latenz als Chrome aufweist und Kino Projector keine Interaktion benötigt.

##Anleitung CMS

Das CMS läuft auf dem Mac Mini Kino Interface. Im Ausstellungsbetrieb zeigt dieser Client das Frontend an, wo die Besucher Filme auswählen können. Um neue Filme ins System einzufügen, muss wie folgt vorgegangen werden:

1. Exit Frontend (iCab)
Tastatur anschliessen und aus iCab ausbrechen

2. Film auf System kopieren
Auf dem Desktop ist ein Link Namens movies, welcher auf den Ort zeigt, wo die Filme auf der HD abgespeichert sind. Hierher muss der Film kopiert werden.

3. Film-Eintrag in DB erstellen
Hierfür Google Chrome öffnen und auf folgende Adresse navigieren: http://localhost:5000/backend

4. Auf Film erstellen klicken
5. Daten eingeben
6. Computer neu starten

### Kino Test-Environment
Das CMS ist für Test-Zwecke auch in einem Test-Modus abrufbar. Dabei wird eine separate Datenbank (***_test) erstellt. Die Kino-Funktionalität ist im Test-Modus so konfiguriert, dass das Kino (http://localhost:5000/cinema) die Socket-Kommunikation mit dem localhost aufrecht erhält. Also die Filme auf der gleichen Maschine wie sie ausgewählt werden abspielt. Dies kann mit dem öffnen eines zusätzlichen Tabs im Browser getestet werden.

Um das CMS und das Kino im Testmodus laufen zu lassen, muss zuerst der Service (siehe LaunchControl) gestoppt werden. Danach das Kino wie folgt aus dem Terminal starten.

```sh
node server.js test
```



