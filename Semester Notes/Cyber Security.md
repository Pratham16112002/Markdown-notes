It is like digital security of computers, servers and data. It's a set of practices and technologies that prevents technologically powered devices from being hacked, damaged or stolen by bad actors on the internet .
## CIA 
<span style='color:red;font-weight:bold;'>Confidentiality</span>
No Unauthorized access or restrict the access to authorized users only. 
This means that sensitive data should not be disclosed to any unauthorized persons or systems. 
**Security measures like encryption**
	By encrypting the data, we make sure that none other than the authorized person can see the data without the key to unlock the encryption. 
**Access Controls** 
	By some access control mechanism we can restrict the access to the data to some specific employees only , rather than every employee of the organization. 
**Authentication** 
	By added some Biometrics, ( 2FA ) before accessing the data might increase its confidentiality of the data. 
**Secure Transmission** 
	By using some secure protocols like HTTPS instead of HTTP and SSL protocol. 
<span style='color:red;font-weight:bold;'>Integrity</span>
Means the make sure the accuracy and reliability of the data . 
No modification of data should be done by any unauthorized person or parties. 
**Security measures like hashing and checksums** 
	Generating a hash value of the data using some crypto-graphic functions and then comparing the hash values at every moment while the data is in transmission. 
**Digital Signatures** : 
	A electronic signature is added with the data while transmission and when receiver receive the data then he/she verify the digital signature and make sure that data is not modified. 
<span style="color:red;font-weight:bold;">Availability</span>
Make sure that data should be available to the right person when he/she needs it.
System should be reliable and accessible anytime.
**Redundancy** 
	My having all the data duplicated in organization makes sure data is accessible anytime, if one server fails the the duplicate data can be transferred immediately. 
**Regular Backups**
	To make sure that in case of any damage to data, data can be easily restored. 
**24x7 Power Availability**
**DOS protection**
	Implementing DOS strategies, like rate limiting and traffic limiting . 
> DDOS and DOS affect the availability of the data. 

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
A computer virus is a program which is used to replicate it-self and spread from one computer device to another. 
Often attaches itself to a legitimate program or files and spread through the computer device fast. 
**Direct infection** : When virus infect the computer system, every time the user open a specific infected program or file. 
**Fast infection** : When virus infects the files whenever any file accessed by the program is infected. 
**Slow infection** : When virus infects any new file or modified document.
## Trojan horse 
It is a program or software which looks legitimate one, but underneath the program is designed to steal the information or deletes the computer data. 
Some trojan horse also creates back-doors in the computer systems. 
### Worms 
worms are more dangerous then viruses. 
Both worms and viruses are malicious program a computer system, without the users consent and replicates themselves . 
<span style='color:red';>Main Difference between virus and worm</span>
1. Virus spread through human action, where worms are self replicating. 
2. Worms are even capable of replicating over user's network ( Called : *Internet worms*) 
3. Worms can also spread to others users in your contact list and copy themselves into every other user in the contact list, it copies itself into email attachments ( Called : *Email worms* ).
### Zombie & Botnets
*Zombies* : These are the system which are already affected by some viruses and the attackers as full control over the system, Can be remotely controlled inorder to perform malicious activities, used for DDOS , phishing , spamming, etc. 
*Botnets* : It is a computer network compromised by a cybercrime group and that group has access to each and every zombie in the network . 
	Botnets are only created by cybercrime group when they need some high computational power for an attack, more likely an DDOS attacks . 

### Adware & Spyware 
*Adware* : These are the malwares which are designed to display advertisement to the user, They are not usually harmful to the computer system but they tends to steal information about the users such as search history, apps he/she uses, etc. 
	Adds corresponding to users behaviour is shown to the user. 
*Spyware* : It is like a adware that spies on what the user is doing collect the information and provide it to the attacker, spyware unlike adware uses users device memory and keep running in the background. 
	The best example of spyware would be keylogger, Adware, Trojan spyware. 

## Denial of service attack 
It a malicious attempt to attack the availability of server hence data, in this attack attacker flood a organization's servers with multiple overwhelming request, server is sometimes tricked into believing that the requests are coming from legitimate users. 
All the resources of the server are interrupted by those request and server is unable to handle the requests of its own users, due to which server becomes unavailable . 

## Ransomware 
It is a type of malicious attack in which some how attacker gains the access to user data and encrypts all the files, In return attacker want ransom in order to get the decryption key to gain access to the system. 
It is also intended to attack the availability of the data. 

## Web attacks
Those malicious attack which tends to attack the web-applications and web-servers, with an intent to exploit the vulnerabilities and steal data or destroy data. 
There are various web-attacks like CSRF, XSS attack , SQLi attack. 

**XSS attack** : In this attack attacker injects malicious client side script into web-pages without their consent, their main task is to steal the users information from that web-application. 
	<span style='color:lightgreen;'>Prevention</span>
	Install web application firewall. 
	Input validation before sending to the web-application. 
	






