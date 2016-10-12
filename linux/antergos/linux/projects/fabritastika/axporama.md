## Fabritastika Axporama

### Beschreibung
Touchscreen, der auch via iPad gesteuert werden kann

### Systemkonfiguration
Komponente              | IP-Address 
----------------------- | ------------- 
TP-Link                 | 192.168.1.10
Tablet (iPad)           | 192.168.1.51 
Intel Nuc               | 192.168.1.50

#### Intel Nuc
user: admin
password: axporama
Applikation: /home/user/axporama/

#### Socket Kommunikation
Die Steuerung iPad => Nuc findet über Websockets statt. Der iPad(192.168.1.51) muss dabei eine socket-Verbindung zum Server(192.168.1.50) haben. 
Das Kommunikations-Schema sieht wie folgt aus:
```sh
/* Browser (iPad) <=> Server <=> Browser (Nuc) */
```

In Fall von axporama wird aber nur eine unidirektionale Kommunikation verwendet:
```sh
/* Browser (iPad) => Server => Browser (Nuc) */
```

#### Environments
Es gibt 3 Modi *dev*, *staging* und *prod*. *dev* und *staging* laufen auf Port 5555, prod auf Port 5000.
Um die Software zu Debuggen kann der Modus wie folgt geändert werden:
```sh
/*dev mode*/
cd /home/user/axporama
node server.js dev
```

#### Autostrt
Der Webserver wird mit dem npm Module *pm2* beim booten gestartet. Die Website ist im Browser unter http://localhost:5000/ abrufbar. 

#### Process Manager
Der Server wird mit dem process manager pm2 beim booten gestartet. Der Server kann mit folgenden Befehlen manuell gestartet oder gestoppt werden:

```sh
/*Server Stoppen*/
pm2 stop server

/*Server Starten*/
pm2 start server
```

#### Tablet (iPad)
Lock Code: 0000
IPad muss mit dem Wireless Netzwerk "axporama" verbunden sein um mit dem Nuc kommunizieren zu können. 
Auf dem Startscreen des iPad ist ein Link abgelegt der auf http://192.168.1.50:5000/tablet zeigt. Dort läuft das Interface vom Tablet.

#### Accesspoint
-IP Address: 192.168.1.10
-Mac Address: 18:A6:F7:8A:E4:6A
-user: admin | pw: axp0rama

### Tmp Client Config Mac Mini
User: user
Pw: macminitweak

Login-Prozess startet app und chrome im Kiosk Modus
Cusrsorcerer versteckt Maus nach 5 Sekunden (Ctrl + Alt +K um Maus temporär wieder anzuzeigen)
