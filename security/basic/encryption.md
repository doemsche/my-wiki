### Symmetric Encryption

Algorithm
-Public

Key
-Secret

AES = Symmetric Alogrithm (Uses 1 key)
The higher the number the stronger the Algorithm

Symmetric Algorithms are used in most encryption systems:
https, full disk encryption, file encryption, Tor, VPN

AES is the standard.

### Asymmetric Encryption
Public and Private Key (Uses 2 keys)

Examples:
-RSA Rivest-Shamir-Adleman
-Elliptic curve cryptosystem (ECC)
-Diffie-Hellman (DH)
-El Gamal

If you encrypt with the private you need the public to decrypt
If you encrypt with the public you need the private to decrypt

When a sender encrypts a message with a recivers public key. Only the receiver can decript the message. => **Condifendiality** => Diskretion

When I encrypt with my private key everybody can read it, but it is clear that I am the source => **Authentication**

### Hash Functions
Hash fn takes as input data of any size and converts it to a fixed size string of characters. (Digest). Hash functions are one way, you cannot convert it back

It provides **Integrity** and detects unintentional modifications.

Fox => crypto hash fn() => DFCD 32498 ... 
Examples of Hash fn:
-MD2, -MD4, -MD5, -havel, -SHA, -SHA1, -SHA256, -SHA384, -SHA512, -tiger
(Today use SHA256 and above)

### Digital Signatues
A digital Signature is a hash value that is encrypted with the senders private key. => Stamp of approval.

It provides:
-**Authentication** (encrypted with private key)
-**Non-Repudiation** (encrypted with private key)
-**Integrity** (because it is hashed)

### SSL and TLS
-SSL => Secure Socket Layer
-TLS => Transport Layer security

SSL and TLS use symmetric and asymmetric encryption combined with hashes and digital signatures and message authetication codes.
SSL is the older protocol TLS the newer.
Both (SSL and TLS) are referred to as SSL => misleading.

https:// Connection is private because of a symetric alogrithm. The keys for the encryption are generated for each connection and are based on a secret negitiation before bytes are exchanged.
Each message transmitted includes a message authentication code (MAC).

forward-secrecy => Diffie Hellman (if server is compromised and no forward-secrecy is **not** available all previous sessions can be read)

#### SSL Configuring a Server:
https://mozilla.github.io/server-side-tls/ssl-config-generator/

### SSL Stripping
Man in the middle attack. Redirects https connection to http.

2 cases ssl-strip reacts to:
-When entering www.facebook.org => 403 redirect to https:// is sent to the browser.
-When making google search and clicking on https:-links

SSL-Stripping can be prevented with VPN/SSH

### HTTPS
HTTP protocol is in plain text
https running http over tls or ssl.

https://www.ssllabs.com/
https://moxie.org/
1) Handshaking phase, where server and client exchange security params.
Client decides wheter it accepts the digital signature of the server.
There are cases where both (client and server) have certificates.

### Digital Certificates
X.509 Most Used Standard for Certs in Web
Certificates Hierarchy up to root => Root Certificates. => Chain of Trust
Browsers contains a whole list of Root-Certificates.
This means: Mozilla, Google or Microsoft trust them not necessarily we!

https://notary.icsi.berkeley.edu/trust-tree/

Nation States will have influence on Certificate Authorities.
=> Fake Certificates
=> Bogus Certificates

Firefox => Add ons => Certificate Patrol
Man in the middle can happen between Vpn Server and Web (fake certificates e.g)
Vpn => Vpn Server => Web

E2EE => End to end encryption

### Steganography
Example: Image (jpg, png...) that contain a secret message. Data is hidden **not encrypted**

With Encryption it is obvious that it is encrypted, with Steganography it is not.

Example => OpenPuff

Quote for security:
Today we were unlucky, but remember we only have to be lucky once. You will have to be lucky always.


