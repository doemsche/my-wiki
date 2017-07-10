# How you are tracked and profiled online

## How does tracking happen

### Most basic way of tracking is IP Address => TCP/IP
### 3rd party connections
### http-referer=> what is my refer
Referer is in Header 
Referer is hierarchical
1px x 1px as Referers

### Cookies & Scripts
First Party Cookie => from original page
Third Party Cookies => from third party sites => ads

If you are logged in to facebook and visit a website, that contains facebook like button, fb knows that you visited the site

If you are logged in to goolge and visit pages that contain google analytics scirpts, google knows that you visited these sites.

If not logged in you are tracked as an ID => (ex: bbc)

Cookie Manager => Firefox

Cookies are used to crack your session, should not contain personal data.

Cookies need to be sent over https so they cannot be used by malicious things.

### Super Cookies => Supercookie
Are designed to be difficult to be detect and removed:
-evercookie
-Cookie in HTML5 anvas tag => RGB 
-Local Shared Objects
-Silverlight Isolated Storage
-Web History
-Http ETags
-Web Cahe
-window.name caching
-Internet Explorer userData Storage
-HTML5 Session Storage
-HTML5 Local Storage
-HTML5 Global Storage
-HTML5 Database Storage via SQLite
-HTML5 Indexed DB
-Java JNLP Persistence Service

ISP can inject Super Cookie in HTTP-Header

### Browser Fingerprinting
https://panopticlick.eff.org/tracker
https://ipleak.net

### Browser Functionality
If you give up functionality you get less trackable
-Geolocation
-Security Features
-send pings
-WebRTC
-Extensions and Plugins
-Browser History

### Tracking Capability
Population Scale Mass Surveillance
Browser-ID that comes from x numbers of IP Addresses => Profiling. Profiles are indirectly linked to you but can be linked to you directly.
From mass surveillance can be done targeted surveillance.
Using profiles you...
Cookies => Supercookies => IP's

### Search Engines
Google has a lot of Channels to track you
Chrome has a BrowserID that tracks and associates you even when not logged in
NID-Cookie & SID
https://tosdr.org
Any free service is monetized in some way

### How to mitigate tracking

https://ixquick.com
meta search engine that stops search engines from tracking you

https://startpage.com
searches google but does not track you => offers proxying => cannot load javascript

https://duckduckgo.com
meta search engine
=> available as a hidden tor-service

https://search.disconnect.me
privacy focused meata-search engine

http://yayc.net => distributed search engine
yacy.net/en/index.html => inst => creates a local proxy on localhost:8090
accuracy is a problem though 
the more people use it the better it'll get

Communication is not encrypted => use VPN, tor

### 2 Step Mitigation
**Step1**
- Enable private browsing
- Use https
- Use privace focues search engines (lxquik, starpage, duckduckgo, disconnect & yacy)

**Step2**
-Hardened Browser
-Use anonymising services (VPNS, JonDonym, Tor etc)







