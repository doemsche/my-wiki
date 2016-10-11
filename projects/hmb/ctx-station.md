# HMB Kontextualisatoren

## Beschreibung
Kontextualisatoren vermitteln Inhalt im Wechselspiel mit der Ausstellung. Die Kontextualisatoren sind verknüpft und können abhängig vom Kontext untereinander Lichtanimationen auslösen. Hierzu laufen zwei Programme auf allen Kontextualisatoren. Einerseits das Interface für die Inhaltsvermittlung (nachstehend ctx-station genannt) und andererseits ein Service, der http-strings für die Lichtanimation empfangen kann (nachstehend http-light-service genannt). Für die Lichtanimationen gibt es 2 verschiedene Modi: "exhibition" und "event" (Siehe weiter unten).

## Client Configuration

### Software / Hardware
Das Basis Image beinhaltet die folgend aufgelisteten Software Pakete, welche auf einem Mac Mini (late 2014) laufen. An allen ctx-stations ist ein Arduino UNO Board via USB angeschlossen, welches einen LED-Strip mit Daten (Lichtanimation) versorgt. 

- Type 'production': (required) Notwendig um als Kontextualisator zu laufen
- Type 'build': (optional) zum builden der individuellen Kontextualisatoren
- Type 'support': (optional) für den Support der Stationen

| Software           | Type        | Purpose
| ------------------ | ----------- | -----------------------
| OSX 10.5.5         | production  | OS
| nodejs             | production  | ctx-server, http-light-service
| iCab               | production  | ctx-server UI
| UPDD Driver        | production  | Touch Screen Hardware Driver
| npm                | production  | package manager nodejs
| StandardFirmata    | production  | Arduino Patch
| LaunchControl      | production  | System Startup
| cliclick           | production  | System Startup
| grunt (node moduel)| build       | for building ctx-staions
| bower (node moduel)| build       | for building ctx-stations
| git                | support     | for updates
| iTerm              | support     | development & support
| atom.io            | support     | development & support
| oh-my-zsh          | support     | development & support
| teamviewer host    | support     | development & support
| Google Chrome      | support     | development & support


## Network Config

Default Gateway: 192.168.1.1
DNS: 8.8.8.8 und 62.2.17.60

Station                 | ID  | IP-Address    | hostname
----------------------- | ----| ------------- |--------------------
Generator               | 1   | 192.168.1.151 | hmb.ctx-01.generator
Diorama                 | 2   | 192.168.1.152 | hmb.ctx-02.diorama
Glocke                  | 3   | 192.168.1.153 | hmb.ctx-03.glocke
Täfeli                  | 4   | 192.168.1.154 | hmb.ctx-04.taefeli
Therapie                | 5   | 192.168.1.155 | hmb.ctx-05.therapie
--- **                  | 6   | none          | --
Heisser Stein *         | 7a  | 192.168.1.157 | hmb.ctx-07a.heisserstein
Heisser Stein (Game)*   | 7b  | 192.168.1.156 | hmb.ctx-07b.heisserstein
Götterhimmel *          | 8   | 192.168.1.158 | hmb.ctx-08.goetterhimmel
Gemellianus (Mosaik)*   | 9   | 192.168.1.159 | hbm.ctx-09.gemellianus
Merker Bianca           | 10  | 192.168.1.160 | hbm.ctx-10.merkerbianca
Transmission            | 11  | 192.168.1.161 | hmb.ctx-11.transmission
Stempeluhr              | 12  | 192.168.1.162 | hmb.ctx-12.stempeluhr
Spind                   | 13  | 192.168.1.163 | hmb.ctx-13.spind
Falck Pokal *           | 14  | 192.168.1.164 | hmb.ctx-14.falckpokal
Badenfahrtkleid  *      | 15a | 192.168.1.165 | hmb.ctx-15a.badenfahrt
Badenfahrtkleid (Game)* | 15b | 192.168.1.166 | hmb.ctx-15b.badenfahrt


- Spezial Stationen *
- Station ohne Interaktion **


### User und Filesystem
Die Ausstellung läuft unter dem User: user. Die relevanten Dateien und Ordner sind:

```sh
/*ctx-station Applikation*/
/User/user/installation/ctx-station/

/*http-light-service Applikaction*/
/User/user/installation/trigger-light-http/

/*Applikations Log Files*/
/User/user/log/

/*Support, Drivers, Software...*/
/User/user/support/
```

### Ctx-Station Build
Grunt (Javascript Task Runner) wird benutzt um die Kontextualisatoren zu builden. Es verfügen immer alle Kontextualisatoren über alle Inhalte. Dh. jeder Client kann als jeden Kontextualisator gebuildet werden und als jeden Kontextualisator laufen. Es gibt Standard-Pakete, die jeder Kontextualisator beinhält und es gibt individuelle Pakete die sich von Station zu Station unterscheiden. Im Gruntfile.js ist eine 'Stage' Funktion beschrieben, die den Build parametrisiert durchführen lässt. Der Build-Prozess kümmert sich um die korrekte Verteilung der Pakete.

Um beispielsweise den 'Generator' (ctx-01) zu builden muss im working directory ../ctx-station folgender Befehl eingegeben werden:
```sh
grunt stage --target=ctx-01
```
Der Command ist wie folgt implementiert: (wobei $ID für die Stations-ID steht. Stationen mit einer id kleiner als 10 müssen mit einer '0' als prefix eingegeben werden).
```sh
grunt stage --target=ctx-$ID
```

Grunt erstellt dann im Verzeichnis ../ctx-station/ einen Ordner namens **dist/**. Da drin ist das Programm, welches über Launchctl gestarter wird und dem iCab Service zur Darstellung der Inhalte dient.

Siehe auch **Git Deployment** und **LaunchControl**


### Ctx-Station Server
Der Sever ist ein NodeJS Express Server, der diverse Routes zur Navigation des Interfaces anbietet. Das Interface läuft unter http://localhost:7000 und verweist standartmässig auf http://localhost:7000/de (deutschsprachige Seite).
Diese Seite ist auch per default als Kiosk-Startpage im iCab eingetragen.
Die Spezial ctx-stations verfügen noch über weitere Routes. Der Entry-point für die special-ctx-stations ist http://localhost:7000/ctx{$ID}idx/.

Siehe auch **LaunchControl**


### Ctx-Station Client
Der Client ist iCab, welcher im Kioskmodus die Inhalte vom oben erwähnten Server konsumiert und darstellt.

### http-light-service

#### Arduino
Die Steuerung des Lichts wird hardware-technisch über ein Arduino UNO und ein LED-Strip (<= Eddi Ergänzugnen nötig?) abgehandelt. Der Softwarepatch, der auf dem Ardunio installiert sein muss, heisst StandardFirmata und findet sich in der Arduino Standard-Distribution unter File -> Examples -> Firmata

#### API
Der http-light-service ist für die Lichtanimation der Kontextualisatoren verantwortlich. Der Service läuft auf der Adresse: http//:0.0.0.0:5000 und lässt sich über eine http-API ansteuern. Für die HMB-Installation gibt es eine fix definierte Animation, die auf allen ctx-stations gleich programmiert ist (hard coded) und wie folgt abrufbar ist:
```sh
/*Http Put-Request an url:*/
http://{$HOST_IP_ADDRESS}:5000/api/animation
```
**Wichtig:** Die API funktioniert nur mit POST-Requests!

#### Konfiguration
Der Service muss konfiguriert werden, da das Arduino UNO von System zu System verschiedene USB-ID's zugewiesen erhalten kann.
Hierfür die settings.default Datei kopieren und in settings.json umbenennen.
Die USB-property mit der Arduino usbmodem-ID versehen.
```sh
{
    "IP": "0.0.0.0",
    "PORT": "5000",
    "USB": "/dev/cu.usbmodem1411"
}
```

### Operation Modes

Device                  | IP-Address     
----------------------- | ------------- 
Tablet                  | 192.168.1.172
Mac Mini Bühne          | 192.168.1.174
Airport                 | 192.168.1.171

**Wichtig: Der Tablet muss im Netzwerk namens '(Eddi wie ist die SSID vom Netzwerk)' sein um die Modi ändern zu können**

Der Modus "exhibition" ist der Standardmodus für den Museums-Betrieb. Im Modus "event" sind auf allen Kontextualisatoren die Animationen deaktiviert. Zusätzlich ist die Rampe beleuchtet. Der Rampen-Mac-Mini ist wie die anderen Kontextualisatoren auch mit einem MacMini plus Arduino und Light-Strip bestückt. Auf ihm läuft der ctx-09. Dieser verfügt über eine speziellen Route: http://localhost:7000/ctx09eventmode

Der Modus kann über das Tablet geändert werden. Auf dem Tablet folgende URL im Browser eingeben: http://192.168.1.174:7000/ctx09eventmode Hier gibt es einen Button der zwischen "exhibition" und "event" toggelt.

Die eigentliche Deaktivierung der Lichtanimation wird auch über die API gesteuert. Das Tablet sendet hierzu folgende Befehle:

```sh
/*Http Put-Request turn on event-mode*/
http://{$HOST_IP_ADDRESS}:5000/api/eventMode/event

/*Http Put-Request turn on exhibition-mode*/
http://{$HOST_IP_ADDRESS}:5000/api/eventMode/exhibition
```

Die Rampen-Beleuchtung wird über die Standard-API gesteuert und mit dem Toggle an- bzw. abgestellt.

### LaunchControl
LaunchControl (launchctl GUI wrapper) ist für folgende 3 Aufgaben zuständig:
- Starten von ctx-station-server
- Clear Log-Files (einmal im Monat)

Der http-light-service lässt sich nicht wie gewünscht über launchctl starten. Die Lichtanimation läuft nicht sauber wenn dieser Service über launchctl gestartet wird. Die Gründe hierfür sind unklar (=> @dos). Der Service wird jeztzt als Automator App namens lightserver geladen und ist im Mac OS X GUI als Tray-Icon (Zahnrad) verfügbar.

Beim System-Startup werden die oben erwähnten Services gestartet. Zu Debug Zwecken können sie auch manuell gestartet werden (Allerdings müssen hierfür die von launchctl gestarteten Services gestoppt sein, weil sonst der Application Port schon besetzt ist).

ctx-station:
```sh
node server.js
```

Die von LaunchControl gestarteten Services loggen Fehler und Output (STDOUT und STDERROR) an folgenden Ort:
```sh
/Users/user/log/
```
Die Log-Files werden einmal im Monat gelöscht.

### Git Deployment
Die Software (ctx-station und http-light-service) aller Stationen kann über Git aktualisiert werden.

Master Branch
```sh
git pull origin master
```
Die Git-Remotes auf welche Leserechte bestehen lauten wie folgt:<br>
origin  git@bitbucket.org:tweaklaborg/ctx-station.git<br>
origin  git@bitbucket.org:tweaklaborg/trigger-light-http.gi

**Wichtig:** Die Station haben nur Leserechte! Änderungen müssen im Original-Git-Repository gemacht werden und danach mit git pull auf die Station geholt werden. Auch muss nach jedem git pull die Station neu gebuildet werden um die Änderungen im Interface (Server und Client) zu reflektieren.


### First Level Support (Fehler die auftreten können)
Case: Kontextualisator startet. Erstes Bild wird nicht geladen. 
Handling: Javascript ist im iCab deaktiviert.
Grund: Unbekannt. Es kommt (sehr selten) vor dass sich Javascript im iCab selber deaktiviert (Power off?)

Case: Licht-Animation geht nicht
Handling: Neu starten und sicherstellen, dass Lichtserver läuft (Zahnrad in Menu Bar)
Grund: Fehler beim automatischen Start vom Lichtserver
