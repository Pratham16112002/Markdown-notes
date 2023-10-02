It is like digital security of computers, servers and data. It's a set of practices and technologies that prevents technologically powered devices from being hacked, damaged or stolen by bad actors on the internet .

## CIA

<span style='color:red;font-weight:bold;'>Confidentiality</span><br>

No Unauthorized access or restrict the access to authorized users only.<br>
This means that sensitive data should not be disclosed to any unauthorized persons or systems.<br>
**Security measures like encryption**<br> - By encrypting the data, we make sure that none other than the authorized person can see the data without the key to unlock the encryption.<br>
**Access Controls**<br> - By some access control mechanism we can restrict the access to the data to some specific employees only , rather than every employee of the organization.
**Authentication** - By added some Biometrics, ( 2FA ) before accessing the data might increase its confidentiality of the data.<br>
**Secure Transmission**<br> - By using some secure protocols like HTTPS instead of HTTP and SSL protocol.<br>
<span style='color:red;font-weight:bold;'>Integrity</span><br>
Means the make sure the accuracy and reliability of the data.<br>
No modification of data should be done by any unauthorized person or parties.<br>
**Security measures like hashing and checksums**<br> - Generating a hash value of the data using some crypto-graphic functions and then comparing the hash values at every moment while the data is in transmission.<br>
**Digital Signatures** :
A electronic signature is added with the data while transmission and when receiver receive the data then he/she verify the digital signature and make sure that data is not modified.<br>
<span style="color:red;font-weight:bold;">Availability</span><br>
Make sure that data should be available to the right person when he/she needs it.<br>
System should be reliable and accessible anytime.<br>
**Redundancy** :
My having all the data duplicated in organization makes sure data is accessible anytime, if one server fails the the duplicate data can be transferred immediately.<br>
**Regular Backups** :
To make sure that in case of any damage to data, data can be easily restored.<br>
**24x7 Power Availability**
**DOS protection** :
Implementing DOS strategies, like rate limiting and traffic limiting.<br>

> DDOS and DOS affect the availability of the data.<br>

## Threats and vulnerabilities

**Threat** : Any potential circumstance or event that can harm an information system by destroying it or disclosing it or stealing from it or changing it.
**Vulnerabilities** : Weakness in the information system that can be exploited by attacker.

## Phishing

It is a cyber crime in which attackers attempt to deceive the individual or organization to disclose their confidential information to them.
Typically involves :

1. Deception : The attackers sometimes impersonate as a trusted entity by sending fake email to the individual or organization .
2. Bait : The attackers try to lure the victim by offering him/her very tempting offer or urgent emergency messages.
3. Clicking link and attachment : Victims are usually asked to click on some link with redirect them to a website which is a counterfeit of the original website inorder to gain control over user information.

## Malware

Are special software which are designed to gain unauthorized access or exploit computer systems or networks or devices , without the consent of user or owner.

### Virus

A computer virus is a program which is used to replicate it-self and spread from one computer device to another.<br>
Often attaches itself to a legitimate program or files and spread through the computer device fast.<br>
**Direct infection** : When virus infect the computer system, every time the user open a specific infected program or file.<br>
**Fast infection** : When virus infects the files whenever any file accessed by the program is infected.<br>
**Slow infection** : When virus infects any new file or modified document.<br>

## Trojan horse

It is a program or software which looks legitimate one, but underneath the program is designed to steal the information or deletes the computer data.<br>
Some trojan horse also creates back-doors in the computer systems.<br>

### Worms

worms are more dangerous then viruses.<br>
Both worms and viruses are malicious program a computer system, without the users consent and replicates themselves.<br>
<span style='color:red;'>Main Difference between virus and worm</span>

1. Virus spread through human action, where worms are self replicating.
2. Worms are even capable of replicating over user's network ( Called : _Internet worms_)
3. Worms can also spread to others users in your contact list and copy themselves into every other user in the contact list, it copies itself into email attachments ( Called : _Email worms_ ).

### Zombie & Botnets

**Zombies** : These are the system which are already affected by some viruses and the attackers as full control over the system, Can be remotely controlled inorder to perform malicious activities, used for DDOS , phishing , spamming, etc.<br>
**Botnets** : It is a computer network compromised by a cybercrime group and that group has access to each and every zombie in the network.<br>
**Botnets** are only created by cybercrime group when they need some high computational power for an attack, more likely an DDOS attacks.<br>

### Adware & Spyware

**Adware** : These are the malwares which are designed to display advertisement to the user, They are not usually harmful to the computer system but they tends to steal information about the users such as search history, apps he/she uses, etc.<br>
Adds corresponding to users behaviour is shown to the user.<br>
**Spyware** : It is like a adware that spies on what the user is doing collect the information and provide it to the attacker, spyware unlike adware uses users device memory and keep running in the background.<br>
The best example of spyware would be keylogger, Adware, Trojan spyware.

## Denial of service attack

It a malicious attempt to attack the availability of server hence data, in this attack attacker flood a organization's servers with multiple overwhelming request, server is sometimes tricked into believing that the requests are coming from legitimate users.<br>
All the resources of the server are interrupted by those request and server is unable to handle the requests of its own users, due to which server becomes unavailable.<br>.

## Ransomware

It is a type of malicious attack in which some how attacker gains the access to user data and encrypts all the files, In return attacker want ransom in order to get the decryption key to gain access to the system.<br>
It is also intended to attack the availability of the data.<br>

## Web attacks

Those malicious attack which tends to attack the web-applications and web-servers, with an intent to exploit the vulnerabilities and steal data or destroy data.<br>
There are various web-attacks like CSRF, XSS attack , SQLi attack.<br>

**XSS attack** :
In this attack attacker injects malicious client side script into web-pages without their consent, their main task is to steal the users information from that web-application.<br>
<span style='color:lightgreen;'>Prevention</span> :

1. Install web application firewall.
2. Input validation and sanitization.
3. Output encoding.
4. Keeping software up to date.
5. Using Content Security Policy.

**DDOS attack** :
It is type of large scale DOS attack in which attacker creates an army of botnets, all the botnets are remotely instructed to attack the web-server at a particular time, all the botnets send multiple requests to construe the web-servers, and make the web-server inaccessible to the original users.<br>
<span style='color:lightgreen;'>Prevention</span> :

1. Implement features like rate limiting.
2. Install web application firewall .
3. Take regular backups of server data.

**SQL Injection Attack** :
It is the most dangerous attack target to a database of the web application.<br>
It occurs when attacker manipulate user input in web-application and send malicious SQL queries on the database.<br>
<span style='color:lightgreen;'>Prevention</span> :

1. Input validation, the data should be well filtered before reaching the database.
2. Least privilege, restrict the data base access to only required or necessary persons only.

**Client Side request forgery** :
In this attack attacker exploit the trust between the website & user's browser.<br>
Attacker tricks the victim into making a request to a different web-application, because of the cookie stored in the victim browser, victim takes advantage of that and make a malicious request for a particular web-application.<br>
Web-server is tricked into believing that request is coming from the legitimate users instead the request is coming from the attacker.<br>

<span style='color:lightgreen;'>Prevention</span> :

1. Anti-CSRF tokens, these token are unique for each session and must be sent with each and every request and the server checks the validity of the that token each time.
2. Content Security Policy, to restrict the which domains are allowed to execute java script on the browser.
3. Same origin policy.

## Email attacks

1. **Email Bombing** : Sending large amount of email in a bulk to a particular user, here we just irritate the user only.
2. **Email Spoofing** : Sending a malicious email to the user which looks like a email from a legitimate person.
3. **Email Hacking** : Finding the password of the user's email.

[OS Seurity](./Security-OS.md)
[Security ConterMeasures](./Security-Counter-Measures.md)
