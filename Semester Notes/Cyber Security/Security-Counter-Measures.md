# Security Counter Measures

## Firewall

Its is the fundamental component of network security, can be defined
as a software application designed to monitor and control the
outgoing and the incomming packets in a network.

It works on the network layer.

It acts as a barrier between the internal network and the outer network.

Its primary function is to allow non-threateing traffic and block malicious
traffic from entering the network.

**Used for** :

1. **Packert Filtering** : It mointers each and every data packet and based on a
   certain criteria such as destination IP address, source IP address,
   port
   numbers. Packets which meet a certain condition are allowed others are blocked.
2. **Logging and monitors** : Firewall logs and network logs allows admin's in
   cyber criminal investigation in case a of cyber attack.
3. **Load Balancing** : In Large organizations when traffic load on a particular
   server is high, then firewall prevent access to that particlular server to
   distribute the traffic evenly.
4. **Access-Control** : By specifiying which devices are allowed to enter the
   network with a access control list (ACL) or white-list which allows
   only specific devices with a particular MAC-address.
5. **Port and Protocol Control** : Firewall can control traffic from a specific
   port or portocol. For example, they can be allowed to accept the traffic from
   port 80 while blocking the traffic from other ports.

## Types of firewalls

**Circuit level Firewalls** :

It provides User Datagram Protocol and Transmission Control Protocol connection securly.
Does not do packet inspection ( Data inside the packet is not monitored ).  
it is relatively quicker way of determing macious content in the data packets.  
It makes sure that only authentice entities are communicating over in the network.  
**Stateful Inspection Firewalls** :

Also called _Dynamic Filtering_, this firewall can detect weather a packet
belongs to a particular session or not. It will only permit the packet if it
belong to a session between two endpoints.  
Can compromise the performance of the network.  
Examine each packet's data in the network.  
Most secure network firewall.

**Network Address Translation Firewall** :

- This type of firewall usually hides the IP address by generating a unique IP
  address for public use.
- Unique IP address is assigned to each device connected to the network.
  For attackers it becomes harder to identify a particular host connected
  to a private network.

**Application-Gateway** :

- Also called proxy servers.
- More secure than the other firewalls.
- Also check the payloads of each data-packet entering the network.
- Can also hide the indentify of each individual host in the private network by
  hiding the IP address of those host.
- Can improve performance & speed of the organizations network by storing the
  frequently visited web-pages into its cache and retrive web-pages directly from
  cache rather than surfing the internet.
- Involes more processing overhead though.
- Best for network logging.
- Various types are open proxy
  (installed in between two conmmunicating entities),
  forward proxy (installed on user private networks) , reverse proxy
  ( installed before web-servers) .

![Proxy](../../assets/Proxyserver.png)

## Intrusion detection system

It is a cyber security strategy which monitors traffic & system activites and
digital assets to indentify and respond to malicious activities and potiential
security threats to the system or network.

The main goal of IDS is the detect unauthorized access, data breaches, data
theft and alert the administrators about them to mitigate them.

### Methods of IDS

1. **Signature based IDS** : Best used to detect known threats, It operates by using a pre-programmed list of known threats called IOC ( Indicator of compromise ).  
    IOC can be certain hashes, malcious domains, suspicous email subjects in term of email security.
   security.  
    In this type IDS searches for source address, destination address, portocol, port number in each and every packet in the system or network.
   A database is created for all the type of IOC that can occur in a network.  
    The pattern of each packet is then matched with the one in the database, if their exist a match then alarm is generated.This method is successfull in detecting known attacks but cannot identify known attacks.  
   Manual Updation is required to add newly explored
   attack pattern to the to the pattern database.
2. **Anomoy based detection** : Integrates Machine Learning Algorithm, algorithm sets a baseline of the normal behavior of the system/network which represents how the system behaves normally, Monitors the behavior of the system.  
   If a behavior of the system is different from predefined behavior then a alarm is generated
   by the network.  
   Suppose an employee which has certain access in a organization performs a activity which is not in scope of his/her capabilities then IDS will generate alarm.  
   Likely to generate false alarams if the IDS is not properly installed on the network or the system.

### Types of IDS

1. **NIDS** : This is a entire network based IDS, Monitor and captures network traffic, detect malicious data present in the packets. Match each packet pattern with the library of known. This system is independent of the operating system, though is does not analyze the encrypted traffic.
2. **HIDS** : Installed on individual hosts.  
   Monitors the packets sent to and from an individual host only and generates
   an alert when suspicious activity happens. A snapshot of the previous system and current system is compared to detect intrusion.

> IDS is kept between the firewall and the network.

### Intrusion prevention system

It has the same functinonality that IDS does, the main difference between both of them is IPS actively defends the network by stopping the attack and also performs alert mechanisms (Tells the packet "You shell not Pass 😁".

It also performs cyclic redundancy check (CRC), and packet defragmentation to clean and maintain the integrity of the data packets.

### Password cracking

It is the method of using application programs to recover deleted or forgotten passwords, attackers also use these applications to maliciously gaining the password of victims and perform unauthorized access to the resources.

1. **Brute Force Attack** : In this type of password cracking user tries all the possible combination of the passwords possible until the correct one is found.
   This approach is called brute force because this technique relays on the computer computing power of guessing the correct password.
   Slow and computationally intensive.  
   Can guess the password for every length.  
   $\color{red}{Prevention :}$  
   Use complex password which are difficult to guess.  
   Use 2FA, such as one-time-password login.  
   _Rate limiting_ to prevent repetated login attempts.

2. **Dictionary Attack** : In this type of attack, attacker maintains his/her own dictionary of all possible password combination.
   The dictionary file is provided to password guessing application programs, the program tries all the words present in the dictionary hoping to get a password match.  
   Fast but limited by the words in the dictionary.  
   Can guess the password for specific length only.

3. **Rainbow Table Attack** : The Attacker maintains a dictionary of all pre-compiled hashes called $\color{green}{Rainbow Tables}$, when the attacker gains control of all the password hashes, the attacker quickly look up for matches in the rainbow tables. If a match is found then attacker sees the corresponding plain text in the rainbow table.  
   Attackers need to know the hashing algorithm used for hashing.

#### Cookie replay attack / Session Hijacking Attack

In this type of attack, the attacker intercepts the commucation between user and and web-application and with the help of valid user session keys present in the local cookies of the victim gains unauthorized access to the web-application or website.
Cookies are small peices of information that are stored in the device that contains the information related to their session, such as session-ID, tokens, other session-related data.
By intercepting cookies, an attacker can impersonate as a legitimate user and potentially gain access to their account.

**Prevention** :

1. Always use HTTPS to make sure cookies are transmitted only through encrypted channels.
2. Secure cookies : enable the secure flag in the cookies to make sure that cookies are always transmitted over secure encrypted channel.
3. Use Security Headers : use security headers like CSP (Content Security Policy).

### Database security threats

Certainly database security is crucial for protecting sensitive information and preventing unauthorized access to the database, data breaches.

1. **Unauthorized access** : <span style='color:red;'>SQL Injection,</span> the attacker tries to manipulate the input fields of the web-application and inject malicious SQL query which leads to unathorized access to database.
2. **Data Leakage** : Attacker try to gain access to the user data stored in database and tries to sell the data to dark-web.
3. **Weak or Unpatched Softwares** : Software application with not the latest update always have known vulnerabilities that attacker will exploit them easily.
4. **DDOS**
5. **Privilege escalation** : People with a restricted privilege try to escalate their privilege to gain unauthorized access.
6. **Secure database backups** : The backups of the database should be done and secured properly to make sure that reliable data can be recovered from the data backup in case of data loss/breach attack.

### SQL Injection attack

In SQL Injection attack, the attacker exploit the vulnerability of unhandled SQL queries of the web-server. The attacker inserts a malicious SQL payload into the input fields of the web-application which has direct access to the database, in order to gain unauthorized access to the database.
**Blind SQL injection attack** : In this type of attack, in which attacker infer the information from the database without directly retriving data from the database.

1. **Boolean type** : The Attacker crafts an sql query to either return true or false for a particular sql query.
2. **Time-based type** : The Attacker crafts the sql query in a way which dely the response of the database on the web-application when some condition is matched, from the response of web-application attacker, infers the information about the database.
3. **Error-based type** : The attacker crafts the sql query in a way which returns a particular error on the web-application when the certain condition is met.

**Out-of-band Sql Injection attack** : The attacker crafts an sql query that redirect the database response to a third party like a fake website or files in the server.

<span style='color:red;'>Consequences :</span>

1. **Data theft** : Attackers can retrive sensitive data from the database.
2. **Data manipulation** : Attackers can also alter the data stored in the database.
3. **Account takeovers** : If the user's password is weak then the attacker can even gain access to the user's account.
4. **Server compromise** : Attackers can also run administrative commands on the server to compromise the entire database.

<span style='color:red;'>Prevention :</span>

1. **Input Validation**
2. **Least Privilege**
3. **Web-application firewalls**
4. **Update the software with latest security patches**

## Data Mining & Cyber security

**Data Mining** : is the process of analyzing information, discovering new patterns and data, predicting future trends.  
It is often used in scientific researches, customer relations, business development even in cyber security field.

Data mining has helped attackers in finding new vulnerabilities & cyber attacks, on the other hand it has also helped cyber security professionals in developing ways to prevent and detect new attacks & vulnerabilities.

Data mining helps you to analyze huge datasets quickly and analyze its hidden patterns, which helps cyber security processionals to develop efficient solutions to malware detection field.  
Though, the final result depends upon the data which is in mining.

Cyber security technique which all possible due to data mining are :

1. **Malware detection** : while developing security softwares, developers are able to increase the speed, analyses, accuracy of the malware detection solutions as well as zero-day attacks.
   There are basically two types of malware detection strategies :

   - **Anomaly detection** : In this type of malware detection the behavior of the system or network is monitored, if any deviation occurs in the normal behavior of the system or network then malware is detected. Can detect known as well as unknown malware attacks.
   - **Misuse detection** : It is usually signature based detection, attacker pattern are constantly matched with the current patterns are generate alert, if any match is found in the system or network. Can only detect only known attacks.

   - **Hybrid detection** : It is the combination of both Anomaly detection and Misuse detection.

2. **Intrusion detection** : Almost all the cybercrimal groups and cybercriminals are always looking to gain unauthorized access to the web-servers of organizations. Data mining techniques can help to analyze the anomolous behavior or patterns in the system or network and prevent those cybercrimes from happening.
   There are basically two types of IDS :
   - Host based.
   - Network based.
3. **Farud detection** : Detection of a fraud is very challenging because these attacks are well-hidden and attacker try new fraud-pattern every time which are difficult to guess.
   But with Data mining technique along with Machine learning, Fraudulent activities can easily be detected.
