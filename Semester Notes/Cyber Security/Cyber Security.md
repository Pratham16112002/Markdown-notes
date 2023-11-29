# Cyber security

It is like digital security of computers, servers and data. It's a set of practices and technologies that prevents technologically powered devices from being hacked, damaged or stolen by bad actors on the internet .

## CIA

<span style='color:red;font-weight:bold;'>Confidentiality</span><br>

No Unauthorized access or restrict the access to authorized users only.<br>
This means that sensitive data should not be disclosed to any
unauthorized persons or systems.<br>
**Security measures like encryption**<br> - By encrypting the data, we make sure that none other than the authorized person can see the data without the key to unlock the encryption.<br>
**Access Controls**<br> - By some access control mechanism we can restrict the access to the data to some specific employees only , rather than every employee of the organization.<br>
**Authentication** - By added some Biometrics, ( 2FA ) before accessing the data might increase its confidentiality of the data.<br>
**Secure Transmission**<br> - By using some secure protocols like HTTPS instead of HTTP and SSL protocol.<br>
<span style='color:red;font-weight:bold;'>Integrity</span><br>
Means the make sure the accuracy and reliability of the data.<br>
No modification of data should be done by any unauthorized person or parties.<br>
**Security measures like hashing and checksums**<br> - Generating a hash value of the data using some crypto-graphic functions and then comparing the hash values at every points to the previously calculated hash value , while the data is in transmission.<br>
**Digital Signatures** :
A electronic signature is added with the data while transmission and when receiver receive the data then he/she verify the digital signature and make sure that data is not modified by any unauthorized means .  
<span style="color:red;font-weight:bold;">Availability</span><br>
Make sure that data should be available to the right person when it is needed.<br>
System should be reliable and accessible anytime.<br>
**Redundancy** :
Having all the data duplicated in organization makes sure data is accessible anytime, if one server fails the the duplicate data can be transferred immediately.<br>
**Regular Backups** :
To make sure that in case of any damage to data, data can be easily restored.  
**24x7 Power Availability** : To ensure that users should not suffer due to power loss the areas.  
**DOS protection** :
Implementing DOS strategies, like rate limiting and traffic migration techniques.<br>

> DDOS and DOS affect the availability of the data.<br>

## Threats and vulnerabilities

**Threat** : Any potential circumstance or event that can harm an information system by destroying it or disclosing it or stealing from it or changing it.
**Vulnerabilities** : Weakness in the information system that can be exploited by attacker.

## Phishing

It is a cyber crime in which attackers attempt to deceive the individual or organization to disclose their confidential information to them.
Typically involves two main types :

1. Deception : The attackers sometimes impersonate as a trusted entity by sending fake email to the individual or organization .
2. Bait : The attackers try to lure the victim by offering him/her very tempting offer or urgent emergency messages.

<span style='color:yellow'>In all the below attacks attacker tricks the victim into beleiving that an trusted entity is communicating with them, by forging the message some how which tricks the user into revailing into disclosing their confidential information</span>

**Types of decpetive phishing attacks** :

1. **Deceptive Phishing** : Type of bait attack, which is targeted to a large group of victim, attacker send the phising emails to all the victims hoping that any one would respond to attackers trap.
2. **Spear Phishing** : This attack is usually targeted to a particular users, attacker has already some information about the user and then forge a phishing email with respect to the information known.
3. **Whailing** : Similar type of spear phishing attack but performed on high-level executives.
4. **Pharming** : Attack make the counterfiet of the original website and tricks the user into loading the fake website to gain access to the credentials of the original website.

## Malware

Are special software which are designed to gain unauthorized access or exploit computer systems or networks or devices , without the consent of user or owner.

### Virus

A computer virus is a program which is used by attackers for malicious purpose, viruses has the ability replicate them-self and spread from one location to another in the computer system.<br>
Often attaches itself to a legitimate program or files and spread through the computer device faster.

**Resident Virus** : This type of virus get stored in computer ram and
and interfare with system operations. These type of viruses are very sneaky, because
they attaches themselves to anti-virus software program files.

**Multi-partite Virus** : If computer system is infected with this type of viruses then, This type fo virus infects the entrie computer system by
performing unauthorized access to system.

**Direct Action Virus** : This type of virus attack a specific type of file only
usually executables (.exe , .com), these type of viruses are very easy to detect and remove.  
These Infected executables gets directly loaded into the main memory, when the files are executed.

**Overwrite Virus** : This type of virus can overwrite content of a files or a
folders.

**Boot Sector Virus** : This type of virus are easy to prevent because they spread through
USB flash drives or infected email attachments, when activated it can also
damage the boot record of the system.

## Logic bombs

Type of malicous softwares, application or programs which perform malicious activities only when certain conditions are meet.  
Attackers sometimes modifies the code of the trusted applications & programs and inject malcious code into it.  
Malicious code written in the software program, or system codes that are triggered only when specific conditions are met.
Can destory/harm/steal/modify/hijack the information on the information systems.<br>
Usually done by insider threats in an organiztions.<br>
Detected by code reviews.

## Trojan horse

It is a programs or softwares which looks legitimate one, but
underneath these programs is designed to steal the information
or deletes the computer data.  
Some trojan horse also creates back-doors in the computer
systems.

### Worms

Type of computer malware or viruses.  
Worms are more dangerous then viruses.  
Both worms and viruses are malicious program a computer system, without the users consent and replicates themselves.<br>
<span style='color:red;'>Main Difference between virus and worm</span>

1. Virus spread through human action, where worms are self replicating do not require any host to replicate itself.
2. Worms are even capable of replicating over user's network ( Called : _Internet worms_)
3. Worms can also spread to others users in your contact list and copy themselves into every other user in the contact list, it copies itself into email attachments ( Called : _Email worms_ ).

### Zombie & Botnets

**Zombies or Remotely-Controlled-Bots** : These are the system which are already affected by some viruses or malware attacks and the attacker ( botmaster ) has full control over the system, Can be remotely controlled inorder to perform malicious activities, used for DDOS , phishing , spamming, etc.  
**Botnets** : It is a computer network compromised by a cybercrime group and that group has access to each and every zombie in the network.
**Botnets** are only created by cybercrime group when they need some high computational power for an attack usually on web-servers of an organizations, more likely an DDOS attacks also used for Cryptocurrency mining and other types of cyber-crimes.

### Adware & Spyware

**Adware** : These are the malwares which are designed to display advertisement to the user, They are not usually harmful to the computer system but they tends to steal information about the users such as search history, apps he/she uses, etc, may also generate AD revenue for the application of web-pages.  
Ads corresponding to users behaviour is shown to the user.
But these adware may contains links to some malcious web-sites.  
**Spyware** : It is like a malicous softwares that spies on what the user is doing collect the information and provide it to the attacker, spyware unlike adware uses users device memory and keep running in the background.<br>
The best example of spyware would be keylogger, Adware, Trojan spyware, Screen scraper.

## Denial of service attack

It a malicious attempt to attack the availability of server
hence data, in this attack attacker flood a organization's
servers with multiple overwhelming request, server
is sometimes tricked into believing that the requests are coming from
legitimate users.  
All the resources of the server are interrupted by those request and server is unable to handle the requests of its own users, due to which server becomes unavailable to the legitimate users.

## Ransomware

It is a type of malicious attack in which some how attacker gains the access to
data and encrypts or steals all the files, In return attacker request for ransom
in order to get the decryption key for encrypted data or data itself.  
It is also intended to attack the availability of the data.  
**There are usually three possible types of Ransomware attacks**

1. **Data loss** : In this type of attack, the attacker steals data, and request for ransom in order to
   provided the data back to victim.
2. **Data breach** : In this type of attack, the attacker steals the data and
   threatens vitcim to leak the data.
3. **Data accessiblity attack** : In this , the attacker gain access to information and
   encrypted it and request for ransom in order to give decryption key.

## Web attacks

Those malicious attack which tends to attack the web-applications and web-servers, with an intent to exploit the vulnerabilities and steal data or destroy data.<br>
There are various web-attacks like CSRF, DDOS ,XSS attack , SQLi attack.<br>

**XSS attack** :
In this attack attacker injects malicious client side script into web-pages of the web-application which gets loaded into the victims browser without their consent, their main task is to steal the users cookie information from the browser cache and gain control over the user session on the web-application on which users has been logged In.<br>
<span style='color:lightgreen;'>Prevention</span> :

1. Install web application firewall.
2. Input validation and sanitization.
3. Output encoding.
4. Keeping software up to date.
5. Using Content Security Policy, we make sure that which origins are allowed to load assets,scripts into the victim's browser.

> Content Security Policy allow users into control which resources to be loaded from the thrid party web-domains.

**DDOS attack** :
It is type of large scale DOS attack in which attacker creates an army of botnet, all the botnets are remotely instructed to attack the web-server at a particular time, all of them start sending multiple requests to construe(interfare) the web-servers, and make the web-server inaccessible to the original legitimate users.<br>
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

1. Anti-CSRF tokens, these token are unique for each session and must be sent with each and every request to the web-application and the server checks the validity of the that token each time when it receives a request with token.
2. Content Security Policy, to restrict the which domains are allowed to execute java script on the browser.
3. Same origin policy.

## Email attacks

1. **Email Bombing** : Sending large amount of email in a bulk to a particular user, here we just irritate the user only.
2. **Email Spoofing** : Sending a malicious email to the user which looks like a email from a legitimate person.
3. **Email Hacking** : Finding the password of the user's email.

[OS Seurity](./Security-OS.md)  
[Security ConterMeasures](./Security-Counter-Measures.md)  
[Privacy_Cyberspace](./Privacy_Cyberspace.md)
