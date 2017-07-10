# Passwords and Authentication

## Crack Passwords

1. Dictionary attacks
check againgst a dictionary

2. Brute force
check every combination possible

3. Hybrid attacks
combine brute force with dict

Methods:
-Combinator Attack => https://hashcat.net/wiki/doku.php?id=combinator_attack
-Rule Based Attacks => https://hashcat.net/wiki/doku.php?id=rule_based_attack
-Analyze => https://thesprawl.org/projects/pack/
-Leet => 1337 
-Markov chain => https://en.wikipedia.org/wiki/Markov_chain
-hydra in Kali 

### Online vs Offline Attacks
Online Attacks => Interacts directly with the cryptosystem. Block IP of attacker after x attempts. After block attacker can change his ip
Online Attacks are only successful against very simple user & passwords

Offline Attacks => attacker has access to the hashes of the passwords
no interaction with crypto system.

Storing passwords in clear-text is a no-go. They must be hashed.
So if they are stolen they still need to be hacked.

### Salting a hash
A hashed password can be combined with a salt-value so they cannot be checked against precomputed hashes (Rainbow tables).

Today nobody uses Rainbow tables (because of size). Today GPU is used over CPU since GPU offers better results in cracking passwords.

Salting is good  and should be used but not as good as you mean.

Key stretching functions use:
-PBKDF2
-bcrypt
-scrypt

use iterations of cryptographic hashes
![](_images/keystretch.png)

### How to steal Password-Hashes
-SQL -Injection
-From Harddisc from Windows

Hashes can be extracted with tools:
-ophcrack
-john the ripper
-hashcat (https://hashcat.net)

```
#revealing the ash algo
hashid 498570923458703824970
```

=> rent AWS for a short amount of time to crack with a lot of power

### Relay Attack
Do not crack the password, but take the request and say it's yours and relay...

### OS Passwords
OS Passwords offer no protection at all => live CD.
If there is physical access to a Computer the password-hashes can simply be replaced.

2-factor Authentication
-YubiKey 4 (limited)
-Whole Disc Encryption

### Password Managers
Password managers offer less attack surface than weak or shared passwords!!
-masterpassword
-keePassX => local Database => no syncing
-lastpass => Cloud Service => Very convenient => biggest attack surface

AVOID:
-patterns (are in every cracking dictionary)
-if a passwords is long enough leet is okay (pw > 20 chars)
-don't use English words
-patterns don't matter if the password is long enough

### Multi Factor Authentication
-auth by knowledge
-auth by ownership
-auth by characteristic

If 2 factors are used => two factor auth

#### Soft Token
TOTP Soft token => Time based one time password 
Google Authenticator supports Open Authtenication (OTP one time password)

If a site is commited to OTP it'll work with Google Authenticator as a second factor auth.

Google Authenticator is an example of an implementation of an OTP-client

https://www.authy.com => Another OTP Client
You must have to have authy on multiple devices (Backup) or you might be locked out forever

#### Hard Tokens
Hardware Implementation of OTP 
-FIDO
-RSA => With Server

#### Future of Passwords
-SQRL => Secure Quick Reliable Login
-CLEF
https://twofactorauth.org
