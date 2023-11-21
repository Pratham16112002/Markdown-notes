## Security OS

Security in OS, refers to the measures and practice taken to protect the Operating system's data and resources from attackers.<br>
It is very critical to maintain the security of the operating systems because, it is the foundation of all the softwares and programs running and once the OS is compromised then attacker has access to each and every data of the computer owner.<br>

#### Port scanning

Ports are the communication end-points through which the computer communicate with the outside network, each port is associated with a specific protocl. <br>
Attacker always moniter the network for open ports and services running on the specific port number, once port is choosen by the hacker then the hacker is ready to launch the various attackes.<br>
This technique is also used by security professionals to test the security of the OS.<br>

#### Network Intrusion or MITM attack

In this attack attacker try to interfare or eavesdrops with the user's or organization network and spoof some request sent to the users, while the users believe that the data is comming from legitimate resources instead it is comming through attacker.<br>
<span style='color:lightblue;'>Prevention</span> :

1. By using HTTPs instead of HTTP.
2. Network segmentation.
3. By implementing DNS security.
4. Keeping softwares up to dates.
5. Using VPN's.

### Rootkits

It is a software or collections of software which are hidden deep within the Operating system, It might hide in the kernal of the Operating system.<br>
Allow attacker to gain control over the entire operating system without knowledge of user.<br>

**Consequences** :

1. Infect device with malwares.
2. Initiate DDOS attack.
3. Disable anti-virus softwares.
4. Take admin rights over the device.
5. Can delete files or event corrupt entire disk.
6. Can also injects some backdoors and keyloggers.

#### How rootkits work

- Rootkit do not spread themselves, attacker uses clandestine methods to inject it in the system, ususally they ask users for root permission over the device.
- Some times rootkits appreas to be a useful software for the operating system and perform malicious activities.
- Rootkit can also destory the boot sectors of a hard drive, preventing user from booting the operating system.

#### Types of rootkits

**User level** :

- Also known as application rootkit.
- **Execution** : It may executes in a same way as the normal computer application do, do not have direct access to the computer resources.
- **Installation** : They do not require administrative privileges while installation can install with only standard permissions.
- **Removal** : Are easier to remove at the user level.
- **Detection** : Can be easily detected by antivirus softwares or even users.

**Kernal level** :

- **Execution** : It executes in the deepest level of the operating system, has unrestricted access to the hardware of computer.
- **Installation** : They must require administrative privileges before installtion, as they need access to kernal.
- **Removal** : Removal of this type of rootkit is challenging even for most of the anti-virus softwares today.
- **Detection** : Can not be easily detected by user or anti-virus because of limited visibility.

#### Bootkit

It is a type of malicious software that affect the master boot record.<br>
Bootloader is the first program which runs when the program starts whose main function is the load the operating system in the main memory.<br>

### Prevention from rootkit

1. **Keep the softwares up to date** : Regular updates are necessary for latest security patches.
2. **Secure Boot** : It is important security meachanism to prevent malicious softwares from loading.
3. **Trusted sources** : Always rely on trusted websites or stores before downloading something.
4. **Take Reguar Backups**
5. **Analysis suspicious behavior** : Notice, anything unusual in the computer system.

## Network security attacks

These attack are usually performed by the cybercriminals to destroy the CIA traid of the network system.<br>

1. **DOS ( Denial of service attack )** : Multiple false request are made to the server in order to crash to web server, thus losing its ability to entertain legitimate users.
2. **Packet Spoofing** : Sending Deceptive emails or messages that appears to come from trusted sources. The goal is to steal confidential information by this attack.
3. **Zero Day Vulnerabilities** : Those softwares or programs which has a vulnerability but that vulnerability is not known to the vendor of the software yet or vendor has no official patch for that vulnerability.
4. **SQL-Injection** : Attacker directly target the database of the web-sever, main aim is too get direct access to the database.
5. **MITM attack** : Attacker tries to interfare and modify the commnunication happening between two endpoints in a network system.

<span style='color:red;'>Prevention</span> :<br>

1. Firewalls.
2. Encryption of data transmitted over the network.
3. **Network segmentation** : Dividing a larger network into smaller sub-networks, as maintaining a smaller network is easir than a larger network.
4. Anti-virus softwares.

### Wireless security

These are the mesasures and protocols to implemented to to protect wireless network from unauthorized access.<br>
Though the information is encryption but anyone can access that information if authentication is not implemented.

#### WEP protocol

**Wired Equivalent Privacy** <br>
It is the eariliest security protocol.<br>
It uses 40 bit encryption key for encrypting the data along with a 24 bit initialization vector.<br>
All traffic in this protocol uses same static key.<br>
The encryption algorithm used is every weak which is RC4 encryption.<br>

![WEP ](../../assets/WEP-ss.png)

#### WPA protocol

**Wifi protected access** <br>
It is better security protocol then WEP. <br>
It uses stronger encryption algorithm like (TKLP).<br>
Uses dynamically changes its key.<br>
Prevents attacker from creating their own encryption key to match the one used to secure the network.<br>
Uses MIC (Message Integrity Check) to make sure that attacker has not altered the packets of the network.<br>

**WPA 2** : <br>

Provides stronger provides even stronger encryption algorithm then WPA.
Uses Advanced Encryption Standard.<br>
WPA 2 is designed to be backward compatible with WPA.

**WPA 3** : <br>

It is the most latest wireless protcol used today.<br>
Uses the most secure encryption algorithm called SAE (Simultaneous Authentication of Equals).<br>
It is resistant to all brute force attacks.<br>
Also comes with the backward compatibility with previous versions of WPA's.<br>
Uses <mark>DPP(Device Provisioning Protocol)</mark> which allows users to share the wifi key using OR codes and NFC's.

## DOS

## DDOS

### Difference between DOS and DDOS attack

| DOS                                                                      | DDOS                                                                  |
| ------------------------------------------------------------------------ | --------------------------------------------------------------------- |
| Denial of service attack.                                                | Distributed Denial of service attack.                                 |
| In DOS a single system is targeted.                                      | In DDOS multiple systems are targeted.                                |
| Victim's machine is loaded with packets sent from a single system.       | Victim's machine is loaded with packets sent from multiple locations. |
| Can be blocked easily, since packets are comming from only one location. | Harder to block, packets are comming from different IP addresses.     |
| Easily traceable                                                         | Difficult to trace                                                    |
