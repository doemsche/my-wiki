### Browser

#### Secure Browsers
-Aviator
-SRWare Iron Browser
-JonDoFox
-Tor
-Epic Privacy Browser
-Comodo Browsers
-- Comodo Ice Dragon (Firefox)
-- Comodo Dragon (Chromium)
-- Comodo Chromium Secure (Chromium)

Google => good for security, bad for Anonymity

Debian => Iceweasel => for of firefox => ice weasel uses debian system libraries

Remove Browser exploit targets:
-Java
-Flash
-Silverlight

-Disable or limit Javascirpt
-Disable or limit PDF reader

Javascript => We need it but it's a security problem

Quick Java Extension Firefox 
about:support => Refresh firefox
about:preferences
about:addons

#### Attack a browser
BeEF and Metasploit on Kali
BeEF => Browser Explotation framework

#### Browser Isolation
-Authentic8
-sirrix

-firefox profiles => use for isolation
-firefox profile switchter
-firefox addon switchy
-firefox extension Priv8 => run tab in sandboxes
-firefox multi fox ?> fun tab in sandboxes

##### Firefox Security Privacy and tracking
about:preferences#privacy
Use Tracking Protection in Private Windows (x)

about:networking => identify networking in browser

Note: Safe Browsing store a mandatory cookie for state use


### Firefox Extensions
#### uBlock Origin
about:memory => show mem usage
settings => im an advanced user
gui => global vs local blocking
uBlock modes refer to https://github.com/gorhill/uBlock

#### uMatrix
For technical users.
uMatrix is similar as uBlock from the same dev as uBlock origin. uMatrix blocks everything and must be configured to work.
uMatrix works with scopes and blocks everything per default. You can accumulatively allow things.
-spoofes the User Agent
-strict https
-delete cookies
-create Rules

#### Request Policy
uBlock uses filters Request Policy blocks all cross site requests requests unless you allow them.

#### Adblock-plus
#### Privacy Badger
Good tool for people who care about privacy.
#### Wot 
Web of trust plugin. It communicates with the WOT server, good for security, bad for privacy

#### No Script
Prevents Cross Site Scripting, Clickjacking
Used by Tor Browser.
Needed to lock down browser completelx
It blocks as well:
-java
-silver light
-flash 
...
-web gl => vulnerabilites

#### Police man addon

#### Purify blocker for IOS

#### Better Privacy
Find and delete LSO Cookie, Flash Cookies, deletes these cookies on exit by default

#### decentraleyes plugin
CDN (Content Delivery Netwrokds)
CDN's are potential trackers
decentraleyes serves cdn content not from cdn source but from self

#### self destructing cookies
deletes cookies and localstorage after closing

#### History Cookies & Supercookies
about:cache => shows information

How to completely wipe (non persistence of browser history and cookies):
-use a live OS (Tails, Knoppix, ...)
-restore snapshot of VM

-CC Cleaner (Mac od and windows)
-Bleachit (Linux and windows)
https://forum.piriform.com/?showtopic=32310
http://www.bleachbit.org/documentation/winapp2_ini
http://www.winapp2.com/


#### Referer Spoofing
refcontrol => controls what header will be sent per site

manually disable deferrer:
about:config 
Network.http.sendRfererHeader => Value 0

uMatrix can spoof the referer as well

### Browser Fingerprinting
#### Random Agent Spoofer
cannot fully guarantee that something else will not leak the true identity

#### HTML5 Canvas Blocking
http://www.browserleaks.com/canvas
canvasblocker


### Certificates and Encryption

#### HTTPS everyewhere addon

about:config
browser.urlbar.tirmURLs => false => always show http or https

#### Certificate Patrol 
Tells you when certificate is updated

#### Calomel SSL Validation
checks encryption of ssl connection

#### Cipherfox
shows info about ssl connection

#### Change what encryption should be trusted
about:config
security.ssl3 => change to false

### Firefox Hardening

Beyond extensions

#### Privacy-Settings 

Info:
about:config
http://kb.mozillazine.org/About:config

Firefox Profilemaker helps to create a Profile as a Zip file
https://ffprofile.com/#firefox_tracking

#### user.js
https://github.com/pyllyukko/user.js
drop user.js in firefox profile directory
user.js changes about:config

#### Jondofox
For Jondonam Anonymous network, but you can turn off the proxy and browse the web => the browser is already hardened



