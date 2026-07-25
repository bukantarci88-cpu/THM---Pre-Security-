# Pre-Security - 2. Network Fundamentals

### **1. Network Fundamentals**

**What is Networking?** Networks are simply things connected.

**What is the Internet?** The Internet is one giant network that consists of many, many small networks within itself.  

- **MAC Address:** A unique hardware address assigned to a device’s network interface card (NIC) during manufacturing. It is used to identify devices on a local network.
- **Ping:** A network diagnostic tool that uses **ICMP (Internet Control Message Protocol)** packets to test connectivity between devices by measuring the time taken for an **echo request** and **echo reply** exchange. It helps determine whether a device is reachable and how reliable the connection is.
- **IP Address:** A logical network address used to identify and communicate with devices on a network. It can be reassigned to different devices over time.

**Local Area Network (LAN) Topologies,  star topology, bus topology, ring topology**

- **Switch:** A network device that connects multiple devices (computers, printers, etc.) within the same network using Ethernet ports.
- **Router:** A device that connects different networks and forwards data between them using routing paths.
- **Subnetting:** A method of dividing a network into smaller sections using a subnet mask to control the number of available IP addresses.

What is the technical term for dividing a network up into smaller pieces? Subnetting

How many **bits** are in a subnet mask? 32

What is the range of a section (octet) of a subnet mask? 0 - 255

What address is used to identify the start of a network? network address

What address is used to identify devices within a network? host address

What is the name used to identify the device responsible for sending data to another network? default gateway

- ARP (Address Resolution Protocol): A protocol that maps an IP address to a MAC address, allowing devices on the same network to communicate with each other.
- DHCP (Dynamic Host Configuration Protocol): A protocol that automatically assigns IP addresses and network settings to devices when they connect to a network.

## **2. OSI Model**

The **OSI** model (or **O**pen **S**ystems **I**nterconnection Model) is an essential model used in networking.  Encapsulation;  key term for when pieces of information get added to data.

**Layer 1 - Physical:** This layer is one of the easiest layers to grasp. Put simply, this layer references the physical components of the hardware used in networking and is the lowest layer that you will find. Devices use electrical signals to transfer data between each other in a binary numbering system

**Layer 2 - Data Link:** The data link layer focuses on the physical addressing of the transmission. It receives a packet from the network layer (including the IP address for the remote computer) and adds in the physical MAC (Media Access Control) address of the receiving endpoint. Inside every network-enabled computer is a Network Interface Card (NIC) which comes with a unique MAC address to identify it.

**Layer 3 - Network:** The third layer of the OSI model (network layer) is where the magic of routing & re-assembly of data takes place (from these small chunks to the larger chunk). Firstly, routing simply determines the most optimal path in which these chunks of data should be sent. Whilst some protocols at this layer determine exactly what is the "optimal" path that data should take to reach a device, we should only know about their existence at this stage of the networking module. Briefly, these protocols include **OSPF** (**O**pen **S**hortest **P**ath **F**irst) and **RIP** (**R**outing **I**nformation **P**rotocol). The factors that decide what route is taken. IP Addresses are dealt with at this layer?

**Layer 4 -** **Transport:** the OSI model plays a vital part in transmitting data across a network and can be a little bit difficult to grasp. When data is sent between devices, it follows one of two different protocols that are decided based upon several factors: TCP, UDP

The **T**ransmission **C**ontrol **P**rotocol (**TCP**). Potentially hinted by the name, this protocol is designed with reliability and guarantee in mind. This protocol reserves a constant connection between the two devices for the amount of time it takes for the data to be sent and received.

| **Advantages of TCP** | **Disadvantages of TCP** |
| --- | --- |
| Guarantees the accuracy of data. | Requires a reliable connection between the two devices. If one small chunk of data is not received, then the entire chunk of data cannot be used. |
| Capable of synchronising two devices to prevent each other from being flooded with data. | A slow connection can bottleneck another device as the connection will be reserved on the receiving computer the whole time. |
| Performs a lot more processes for reliability. | TCP is significantly slower than UDP because more work has to be done by the devices using this protocol. |

**U**ser **D**atagram **P**rotocol (or **UDP** for short). This protocol is not nearly as advanced as its brother - the TCP protocol. It doesn't boast the many features offered by TCP, such as error checking and reliability. In fact, any data that gets sent via UDP is sent to the computer whether it gets there or not. 

| **Advantages of UDP** | **Disadvantages of UDP** |
| --- | --- |
| UDP is much faster than TCP. | UDP doesn't care if the data is received. |
| UDP leaves the application layer (user software) to decide if there is any control over how quickly packets are sent. | It is quite flexible to software developers in this sense. |
| UDP does not reserve a continuous connection on a device as TCP does. | This means that unstable connections result in a terrible experience for the user. |

**Layer 5 - Session: It** will begin to create and maintain the connection to other computer for which the data is destined. When a connection is established, a session is created. Whilst this connection is active, so is the session. The session layer is also responsible for closing the connection if it hasn't been used in a while or if it is lost. Additionally, a session *can* contain "checkpoints," where if the data is lost, only the newest pieces of data are required to be sent, saving bandwidth.

**Layer 6 - Presentation:** the OSI model is the layer in which standardisation starts to take place. Because software developers can develop any software such as an email client differently, the data still needs to be handled in the same way — no matter how the software works. This layer acts as a translator for data to and from the application layer (layer 7). The receiving computer will also understand data sent to a computer in one format destined for in another format. For example, when you send an email, the other user may have another email client to you, but the contents of the email will still need to display the same.

**Layer 7 – Application:** The user-facing layer that provides network services to applications, using protocols such as **HTTP, HTTPS, DNS, FTP, and SMTP**. 
The application layer of the OSI model is the layer that you will be most familiar with. This familiarity is because the application layer is the layer in which protocols and rules are in place to determine how the user should interact with data sent or received.

# **3. Packets & Frames**

- **Packet:** A unit of data at **Layer 3 (Network Layer)** that contains an **IP header** and the actual data (payload) being transmitted across networks.
- **Frame:** A unit of data at **Layer 2 (Data Link Layer)** that encapsulates a packet and adds information such as **source and destination MAC addresses** for local network communication.
- **Headers:** Additional information attached to packets or frames that helps devices route, deliver, and process data correctly across a network.

| **Header** | **Description** |
| --- | --- |
| Time to Live | This field sets an expiry timer for the packet to not clog up your network if it never manages to reach a host or escape! |
| Checksum | This field provides integrity checking for protocols such as TCP/IP. If any data is changed, this value will be different from what was expected and therefore corrupt. |
| Source Address | The IP address of the device that the packet is being sent **from** so that data knows where to **return to**. |
| Destination Address | The device's IP address the packet is being sent to so that data knows where to travel next. |

# 4. TCP/IP (The Three-Way Handshake);

| **Step** | **Message** | **Description** |
| --- | --- | --- |
| 1 | SYN | A SYN message is the initial packet sent by a client during the handshake. This packet is used to initiate a connection and synchronise the two devices together (we'll explain this further later on). |
| 2 | SYN/ACK | This packet is sent by the receiving device (server) to acknowledge the synchronisation attempt from the client. |
| 3 | ACK | The acknowledgement packet can be used by either the client or server to acknowledge that a series of messages/packets have been successfully received. |
| 4 | DATA | Once a connection has been established, data (such as bytes of a file) is sent via the "DATA" message. |
| 5 | FIN | This packet is used to *cleanly (properly)* close the connection after it has been complete. |
| # | RST | This packet abruptly ends all communication. This is the last resort and indicates there was some problem during the process. For example, if the service or application is not working correctly, or the system has faults such as low resources. |

TCP packets contain various sections of information known as headers that are added from encapsulation. Let's explain some of the crucial headers in the table below:

| Header | Description |
| --- | --- |
| Source Port | This value is the port opened by the sender to send the TCP packet from. This value is chosen randomly (out of the ports from 0-65535 that aren't already in use at the time). |
| Destination Port | This value is the port number that an application or service is running on the remote host (the one receiving data); for example, a webserver running on port 80. Unlike the source port, this value is not chosen at random. |
| Source IP | This is the IP address of the device that is sending the packet. |
| Destination IP | This is the IP address of the device that the packet is destined for. |
| Sequence Number | When a connection occurs, the first piece of data transmitted is given a random number. We'll explain this more in-depth further on. |
| Acknowledgement Number | After a piece of data has been given a sequence number, the number for the next piece of data will have the sequence number + 1. We'll also explain this more in-depth further on. |
| Checksum | This value is what gives TCP integrity. A mathematical calculation is made where the output is remembered. When the receiving device performs the mathematical calculation, the data must be corrupt if the output is different from what was sent. |
| Data | This header is where the data, i.e. bytes of a file that is being transmitted, is stored. |
| Flag | This header determines how the packet should be handled by either device during the handshake process. Specific flags will determine specific behaviours, which is what we'll come on to explain below. |

The **U**ser **D**atagram **P**rotocol (**UDP**) is another protocol that is used to communicate data between devices. Unlike its brother TCP, UDP is a **stateless** protocol that doesn't require a constant connection between the two devices for data to be sent. For example, the Three-way handshake does not occur, nor is there any synchronisation between the two devices.

| **Advantages of UDP** | **Disadvantages of UDP** |
| --- | --- |
| UDP is much faster than TCP. | UDP doesn't care if the data is received or not. |
| UDP leaves the application (user software) to decide if there is any control over how quickly packets are sent. | It is quite flexible to software developers in this sense. |
| UDP does not reserve a continuous connection on a device as TCP does. | This means that unstable connections result in a terrible experience for the user. |

UDP packets are much simpler than TCP packets and have fewer headers. However, both protocols share some standard headers, which are what is annotated in the table below:

| **Header** | **Description** |
| --- | --- |
| Time to Live (TTL) | This field sets an expiry timer for the packet, so it doesn't clog up your network if it never manages to reach a host or escape! |
| Source Address | The IP address of the device that the packet is being sent from, so that data knows where to return to. |
| Destination Address | The device's IP address the packet is being sent to so that data knows where to travel next. |
| Source Port | This value is the port that is opened by the sender to send the UDP packet from. This value is randomly chosen (out of the ports from 0-65535 that aren't already in use at the time). |
| Destination Port | This value is the port number that an application or service is running on the remote host (the one receiving the data); for example, a webserver running on port 80. Unlike the source port, this value is not chosen at random. |
| Data | This header is where data, i.e. bytes of a file that is being transmitted, is stored. |

# **5. Protocols**

| **Protocol** | **Port Number** | **Description** |
| --- | --- | --- |
| **F**ile **T**ransfer **P**rotocol (**FTP**) | 21 | This protocol is used by a file-sharing application built on a client-server model, meaning you can download files from a central location. |
| **S**ecure **Sh**ell (**SSH**) | 22 | This protocol is used to securely login to systems via a text-based interface for management. |
| **H**yper**T**ext Transfer Protocol (**HTTP**) | 80 | This protocol powers the World Wide Web (WWW)! Your browser uses this to download text, images and videos of web pages. |
| **H**yper**T**ext **T**ransfer **P**rotocol **S**ecure (**HTTPS**) | 443 | This protocol does the exact same as above; however, securely using encryption. |
| **S**erver **M**essage **B**lock (**SMB**) | 445 | This protocol is similar to the File Transfer Protocol (FTP); however, as well as files, SMB ****allows you to share devices like printers. |
| **R**emote **D**esktop **P**rotocol (**RDP**) | 3389 | This protocol is a secure means of logging in to a system using a visual desktop interface (as opposed to the text-based limitations of the SSH protocol). |

# 6. Firewall

A firewall is a device within a network responsible for determining what traffic is allowed to enter and exit. Think of a firewall as border security for a network. An administrator can configure a firewall to **permit** or **deny** traffic from entering or exiting a network based on numerous factors such as:

- Where the traffic is coming from? (has the  been told to accept/deny traffic from a specific network?)
- Where is the traffic going to? (has the  been told to accept/deny traffic destined for a specific network?)
- What port is the traffic for? (has the  been told to accept/deny traffic destined for port 80 only?)
- What protocol is the traffic using? (has the  been told to accept/deny traffic that is ,  or both?)
    
     
    
    | **Firewall Category** | **Description** |
    | --- | --- |
    | Stateful | **Stateful Firewall:** A firewall that monitors and analyzes the **entire connection** rather than individual packets. It tracks the state of active sessions, makes dynamic security decisions based on connection behavior, and can block all traffic from a device if the connection is identified as malicious. While more secure, it requires more system resources than a stateless firewall. |
    | Stateless | **Stateless Firewall:** A firewall that inspects **each packet individually** based on predefined rules, without tracking the state of a connection. It uses fewer resources and is effective for handling large volumes of traffic, such as **DDoS attacks**, but is less intelligent because it cannot analyze the overall context or behavior of a connection. |

What layers of the OSI model do firewalls operate at?

For this answer, just provide the numbers in ascending order, separated by an ampersand (&) 3$4

What category of firewall inspects the **entire connection**? stateful

What category of firewall inspects individual packets? stateless

# 7. VPN

A **V**irtual **P**rivate **N**etwork (or **VPN** for short) is a technology that allows devices on separate networks to communicate securely by creating a dedicated path between each other over the Internet (known as a tunnel). Devices connected within this tunnel form their own private network.

| **Benefit** | **Description** |
| --- | --- |
| Allows networks in different geographical locations to be connected. | For example, a business with multiple offices will find VPNs beneficial, as it means that resources like servers/infrastructure can be accessed from another office. |
| Offers privacy. | **VPN (Virtual Private Network):** A technology that encrypts internet traffic, creating a secure connection between devices and protecting data from interception or snooping. VPNs are especially useful on **public Wi-Fi networks**, where they help keep online activity private and secure. |
| Offers anonymity. | **VPNs for Privacy & Anonymity:** VPNs help journalists, activists, and everyday users protect their online activity by encrypting traffic and hiding it from ISPs and other intermediaries. However, the level of privacy depends on the VPN provider's policies—if a VPN logs user activity, it can reduce or eliminate the anonymity benefits it is intended to provide. |

What VPN technology **only** encrypts & provides the authentication of data? PPP

What VPN technology uses the IP framework? IPsec