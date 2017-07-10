# Email Security

## Clients Protocols and Authentication
Email is fundamentally broken and cannot be fixed.
Email is from a time when security was not thought of

If everybody would switch to a secure Messaging System tomorrow, the problem d be solved, but since this is not going to happen, we are stuck with a broken sytem called email.

##Client vs. Web Access to Email
###Web-Access:
Protocol: https (SSL/TLS encrypted)
Authentication: Server (Certificate), Cleint (Password/2FA)

###Email-Client:

**SENDING**
Protocols:
1. IMAP port:143 (unencrypted) => do not use
2. POP port:110 (unencrpyted) => do not use
3. IMAP port 993 (SSL/TLS encrypted)
4. POP3 port 995 (SSL/TLS encrypted)

Authentication:
Server: (Certificate)
Client: Password/2FA/NLTM/OAuth2

IMAP => for multiple devices (Emails are synced), Server has Master Copy
POP => Downloads Emails to a single Client and deletes it form the server

**RECEIVING**
Protocols:
1. SMTP port 25 (unencrypted) => do not use
2. STARTTLS 587 (SSL/TLS encrypted)
3. SMTP port 465 (SSL/TLS encrypted)

Authentication:
Server: (Certificate)
Client: Password, 2FA /NLTM /OAutch2 ...

##Email Weaknesses
-SSL/TLS is relatively easy to crack
-Mails are stored unencrypted (local and server-side)
-Communication btween SENDER_SERVER and RECEIVER_SERVER are not necessairly encrypted.
-Email is like a postcard, they can be read
-Email has no quality of service => can be spoofed (https://emkei.cz)
-Cannot be sent anonymously (only pseudo anonymously)

##OpenPGP (Pretty Good Privacy)
It protects emails in transport and to a lesser extend in storage
![](_images/pgp.png)
If implemented correctly it is end to end encryption
Both sides need to have PGP (Install software)

###What is PGP
-OpenPGP is a standard that can be implemented
-GnuPG (OpenPGP) implements that standard (OpenSource)
![](_images/encrypt_pgp.png)
Uses public private key => hybrid crypto system
The private key is used to decrypt and digitally sign emails
The public key is public and should be shared with everybody who wants to send you private emails.
![](_images/decrypt_pgp.png)

###Setup Client
-Thunderbird and the addon Enigmail

####Win
https://ssd.eff.org/en/module/how-use-pgp-windows

####Mac
http://notes.jerzygangi.com/the-best-pgp-tutorial-for-mac-os-x-ever/
https://ssd.eff.org/en/module/how-use-pgp-mac-os-x

###Linux
https://ssd.eff.org/en/module/how-use-pgp-linux

#### Webmail 
https://www.mailvelope.com
chrome and firefox extension
google end-to-end

### 
-When you delete the private key, people can still send you encrypted mail to the public key, but you can no more decrypt 
-disable HTML since this can interfere with the encryption
-Allow Remote content must not be checked
-Kleopatra => Key Manager
-meta-data (subject and headers) are not encrypted
-DRAFT => Be aware that they propably are not saved encrypted and imapped to the server unencrypted







