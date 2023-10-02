## Security Counter Measures

### Firewall

Its is the fundamental component of network security, can be defined as a software application designed to monitor and control the outgoing and the incomming packets in a network.<br>

It acts as a barrier between the internal network and the outer network.<br>

Its primary function is to allow non-threateing traffic and block malicious traffic into the network.

**Used for** : <br>

1. **Packert Filtering** : It mointers each and every data packet and based on a certain criteria such as destination IP address, source IP address, port numbers. Packets which meet a certain condition are allowed others are blocked.
2. **Logging and monitors** : Firewall logs and network logs allows admin's in cyber criminal investigation in case a of cyber attack.
3. **Load Balancing** : In Large organizations when traffic load on a particular server is high, then firewall prevent access to that particlular server to distribute the traffic evenly.
4. **AccessControl** : By specifiying which devices are allowed to enter the network with a network control list (ACL).
5. **Port and Protocol Control** : Firewall can control traffic from a specific port or portocol. For example, they can be allowed to accept the traffic from port 80 while blocking the traffic from other ports.

##### Circuit level Firewalls

It provides User Datagram Protocol and Transmission Control Protocol connection securly.

##### Stateful Inspection Firewalls

Also called <mark>Dynamic Filtering</mark>, this firewall can detect weather a packet belongs to a particular session or not. It will only permit the packet if it belong to a session between two endpoints. <br.

##### Network Address Translation Firewall

- This type of firewall usually hides the IP address by generating a unique IP address for public use.<br>
- Unique IP address is assigned to each device connected to the network. For attackers it becomes harder to identify a particular host connected to a private network.

## Intrusion detection system

It is a cyber security strategy which monitors traffic & system activites and digital assets to indentify and respond to malicious activities and potiential security threats to the system or network.<br>

The main goal of IDS is the detect unauthorized access, data breaches, data theft and alert the administrators about them to mitigate them. <br>

### Methods of IDS

1. **Signature based IDS** : In this type IDS searches for source address, destination address, portocol, port number in each and every packet in the system or network. <br> A database is created for all the type of attack pattern that can occur in a packet.<br> The pattern of each packet is then matched with the one in the database, if their exist a match then alarm is generated.<br>This method is successfull in detecting known attacks but cannot identify known attacks.<br> Manual Updation is required to add newly generated attack pattern to the system.<br>
2. **Anomoy based detection** : monitors the behavior of the system.<br> If a behavior of the system is different from predefined behavior then a alarm is generated by the network.<br> Suppose an employee which has certain access in a organization performs a activity which is not in scope of his/her capabilities then IDS will generate alarm.<br>

### Types of IDS

1. **NIDS** : This is a entire network based IDS, Monitor and captures network traffic, detect malicious data present in the packets. Match each packet pattern with the library of known. <br> This system is independent of the operating system, though is does not analyze the encrypted traffic.
2. **HIDS** : Installed on individual hosts.<br> Monitors the packets sent to and from an individual host only and generates an alert when suspicious activity happens. A snapshot of the previous system and current system is compared to detect intrusion.

> IDS is kept between the firewall and the network.

### Intrusion prevention system

It has the same functinonality that IDS does, the main difference between both of them is IPS actively defends the network by stopping the attack and also performs alert mechanisms (Tells the packet "You shell not Pass 😁".<br>
It also performs cyclic redundancy check (CRC), and packet defragmentation to clean and maintain the integrity of the data packets.