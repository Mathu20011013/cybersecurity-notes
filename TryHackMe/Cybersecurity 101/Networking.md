
# **OSI Model (Open Systems Interconnection)**

## **1. What is the OSI Model?**

The **OSI Model** is a networking model developed by the International Organization for Standardization (ISO). It explains how data travels between devices over a network.

It divides network communication into **7 layers**, with each layer performing a specific task.

**Simple example:** When you open a website, several networking processes work together to send your request from your computer to the web server and return the webpage.

## **2. The Seven Layers of the OSI Model**

**P**lease **D**o **N**ot **T**hrow **S**pinach **P**izza **A**way.

|Layer|Name|Main Function|
|---|---|---|
|7|Application|Provides network services to applications|
|6|Presentation|Handles data format, encryption and compression|
|5|Session|Establishes and manages communication sessions|
|4|Transport|Provides end-to-end data delivery|
|3|Network|Handles IP addressing and routing|
|2|Data Link|Transfers data between devices on the same network|
|1|Physical|Transmits raw bits through physical media|

## **3. Explanation of Each Layer**

### **Layer 1 – Physical Layer**

**Main purpose:** Transmits raw binary data (0s and 1s) through physical media.

- Deals with cables, connectors, signals and radio waves.
    
- Data travels through electrical, optical or wireless signals.
    

**Examples:**

- Ethernet cables
    
- Fibre optic cables
    
- Wi-Fi radio signals (2.4 GHz, 5 GHz and 6 GHz)
    

**Simple example:** The physical cable or Wi-Fi signal carries data from your laptop to the network device.

### **Layer 2 – Data Link Layer**

**Main purpose:** Transfers data between devices on the same network segment.

- Uses **MAC addresses** to identify network interfaces.
    
- Handles communication between directly connected network devices.
    
- Data unit: Frame.
    

**Protocols and standards:**

- Ethernet (IEEE 802.3)
    
- Wi-Fi (IEEE 802.11)
    

**MAC Address:**

A MAC address is a 6-byte hardware address, usually written in hexadecimal.

Example:

```
00:1A:2B:3C:4D:5E
```

- First 3 bytes generally identify the manufacturer.
    
- Last 3 bytes identify the network interface within that manufacturer's address allocation.
    

**Simple example:** Two computers connected to the same network switch communicate using MAC addresses at Layer 2.

### **Layer 3 – Network Layer**

**Main purpose:** Transfers data between different networks using logical addressing and routing.

- Uses IP addresses to identify devices.
    
- Routers forward packets between networks.
    
- Determines the path data should take.
    

**Protocols:**

- IP (Internet Protocol)
    
- ICMP (Internet Control Message Protocol)
    
- IPsec (Internet Protocol Security)
    

**Simple example:** Your laptop in Sri Lanka communicates with a web server in another country. Routers help forward the data between different networks.

**Remember:** Layer 3 = IP addresses + Routing.

### **Layer 4 – Transport Layer**

**Main purpose:** Provides end-to-end communication between applications running on different devices.

- Breaks data into smaller segments.
    
- Uses port numbers to identify applications.
    
- Supports flow control and error handling.
    

**Main protocols:**

|TCP|UDP|
|---|---|
|Connection-oriented|Connectionless|
|Reliable delivery|No guarantee of delivery|
|Maintains data order|No guarantee of order|
|Used for reliable communication|Used when low delay is important|

**Examples:**

- TCP – Web communication (HTTP/HTTPS), file transfers.
    
- UDP – DNS queries, real-time voice and video communication.
    

**Simple example:** When downloading a file, TCP helps ensure the data arrives correctly and in order.

### **Layer 5 – Session Layer**

**Main purpose:** Establishes, maintains and synchronises communication sessions between applications.

- Starts communication sessions.
    
- Maintains active sessions.
    
- Helps manage session recovery and synchronisation.
    

**Protocols / examples:**

- NFS (Network File System)
    
- RPC (Remote Procedure Call)
    

**Simple example:** A remote application establishes a communication session with another system and maintains that session while exchanging information.

### **Layer 6 – Presentation Layer**

**Main purpose:** Ensures data is in a format that the application can understand.

Handles:

- Data encoding.
    
- Encryption and decryption.
    
- Data compression and decompression.
    

**Examples / standards:**

- ASCII and Unicode – Character encoding.
    
- JPEG, PNG and GIF – Image formats.
    
- MIME – Email attachment and content encoding.
    
- MPEG – Multimedia encoding.
    

**Simple example:** When you send an image through email, the image uses a format such as JPEG, and MIME helps represent and attach it to the email.

### **Layer 7 – Application Layer**

**Main purpose:** Provides network services directly to applications used by people.

It allows applications to communicate over a network.

**Important protocols:**

|Protocol|Purpose|
|---|---|
|HTTP|Transfers web pages and web data|
|HTTPS|Secure web communication|
|FTP|File transfer|
|DNS|Converts domain names into IP addresses|
|SMTP|Sends emails|
|POP3|Retrieves emails|
|IMAP|Accesses and manages emails|

**Simple example:** When you enter `google.com` in your browser, the browser uses application-layer protocols such as HTTP/HTTPS to communicate with the web server.

## **4. OSI Model – Quick Revision Table**

|Layer|Name|Key Concept|Examples|
|---|---|---|---|
|7|Application|Network services|HTTP, FTP, DNS, SMTP|
|6|Presentation|Encoding, encryption, compression|Unicode, JPEG, MIME|
|5|Session|Session management|NFS, RPC|
|4|Transport|End-to-end delivery|TCP, UDP|
|3|Network|IP addressing and routing|IP, ICMP, IPsec|
|2|Data Link|MAC addressing and frames|Ethernet, Wi-Fi|
|1|Physical|Signals and transmission|Cables, radio waves|

## **5. Important Concepts to Remember**

- **Layer 1:** Physical transmission of bits.
    
- **Layer 2:** MAC addresses and communication within the same network segment.
    
- **Layer 3:** IP addresses and routing between networks.
    
- **Layer 4:** TCP, UDP and port numbers.
    
- **Layer 5:** Establishes and manages sessions.
    
- **Layer 6:** Data formatting, encryption and compression.
    
- **Layer 7:** Network services used by applications.
    

### **Common Networking Terms**

|Term|Meaning|
|---|---|
|MAC Address|Hardware address of a network interface|
|IP Address|Logical address used to identify a device on an IP network|
|Router|Forwards packets between networks|
|Switch|Connects devices within a LAN|
|Port Number|Identifies a particular application or service|
|Packet|Data unit commonly associated with Layer 3|
|Frame|Data unit associated with Layer 2|
# **TCP/IP Model**

## **1. What is the TCP/IP Model?**

- **TCP/IP** stands for Transmission Control Protocol / Internet Protocol.
    
- Developed in the **1970s by the US Department of Defense (DoD)**.
    
- It is an implemented networking model that explains how devices communicate over networks, including the Internet.
    
- It was designed to keep networks working even when some parts become unavailable.
    

**Key idea:** TCP/IP allows data to travel between devices even when network routes change.

## **2. Four Layers of the TCP/IP Model**

The TCP/IP model has **4 layers**, from top to bottom.

|Layer|Main Function|Example Protocols|
|---|---|---|
|**4. Application**|Provides network services to applications|HTTP, HTTPS, FTP, SMTP, DNS, SSH|
|**3. Transport**|Manages communication between devices|TCP, UDP|
|**2. Internet**|Handles IP addressing and routing between networks|IP, ICMP, IPsec|
|**1. Link**|Handles communication with the directly connected network|Ethernet, Wi-Fi|

## **3. TCP/IP and OSI Model Mapping**

The TCP/IP model combines some OSI layers.

|TCP/IP Model|Corresponding OSI Layers|
|---|---|
|Application|Layer 7 – Application, Layer 6 – Presentation, Layer 5 – Session|
|Transport|Layer 4 – Transport|
|Internet|Layer 3 – Network|
|Link|Layer 2 – Data Link|

**Important:** The TCP/IP four-layer model does not define a separate Physical Layer (OSI Layer 1).

## **4. Four-Layer vs Five-Layer TCP/IP Model**

Some networking textbooks use a **five-layer model** by separating the Physical Layer from the Link Layer.

1. Application
    
2. Transport
    
3. Network
    
4. Link
    
5. Physical
    

## **5. Important Protocols to Remember**

|Protocol|Purpose|
|---|---|
|HTTP / HTTPS|Access websites|
|FTP|Transfer files|
|SMTP|Send emails|
|POP3 / IMAP|Receive and manage emails|
|SSH|Secure remote access|
|TCP|Reliable data delivery|
|UDP|Fast communication without guaranteed delivery|
|IP|Addressing and routing|
|ICMP|Network error reporting and diagnostics|
|IPsec|Secure IP communication|

## **6. Key Points for Revision**

- TCP/IP is a practical networking model used for Internet communication.
    
- It has **4 main layers** in RFC 1122.
    
- The Application Layer combines OSI Layers 5, 6 and 7.
    
- The Internet Layer corresponds to OSI Layer 3.
    
- The Link Layer corresponds to OSI Layer 2.
    
- Some textbooks use a five-layer model by adding the Physical Layer.
    
- The next topics are **IP (Internet Layer), TCP and UDP (Transport Layer)**.
# **IP Address (IPv4)**

## **1. What is an IP Address?**

- An **IP address** is a unique logical address used to identify a device on a network.
    
- It allows devices to find and communicate with each other.
    
- IPv4 is the most commonly used IP version.
    

## **2. IPv4 Structure**

- IPv4 uses **32 bits (4 octets)**.
    
- Each octet contains 8 bits and has a value from **0–255**.
    
- Example: `192.168.1.10`
    

|Address|Meaning|
|---|---|
|`192.168.1.0`|Network address|
|`192.168.1.10`|Host address (example)|
|`192.168.1.255`|Broadcast address|

- IPv4 supports approximately **4.3 billion addresses**.

## **3. Subnet and Subnet Mask**

- **Subnet:** A smaller network within a larger network.
    
- **Subnet mask:** Identifies which part of an IP address represents the network and which part represents the host.
    

Example:

```
IP Address:  192.168.66.89
Subnet Mask: 255.255.255.0
CIDR:        /24
```

- `/24` means the first 24 bits identify the network.
    
- Network address: `192.168.66.0`
    
- Broadcast address: `192.168.66.255`
    
- Usable host range: `192.168.66.1 – 192.168.66.254`
    

## **4. Public vs Private IP Addresses**

|Type|Meaning|
|---|---|
|Public IP|Used to communicate over the Internet|
|Private IP|Used inside local networks (LANs)|

**Private IPv4 ranges (RFC 1918) – Memorise these:**

|Range|CIDR|
|---|---|
|`10.0.0.0 – 10.255.255.255`|`10.0.0.0/8`|
|`172.16.0.0 – 172.31.255.255`|`172.16.0.0/12`|
|`192.168.0.0 – 192.168.255.255`|`192.168.0.0/16`|

- Private IP devices access the Internet through a router using **NAT (Network Address Translation)**.

## **5. Finding Your IP Address**

|Operating System|Command|
|---|---|
|Windows|`ipconfig`|
|Linux|`ip a` or `ip address show`|
|Linux (older command)|`ifconfig`|

## **6. Routing**

- **Router:** A network device that forwards data packets between different networks.
    
- It operates at **OSI Layer 3 (Network Layer)**.
    
- It checks the destination IP address and selects the appropriate route to forward packets.
    

**Example:** When your laptop accesses a website, the packets may pass through several routers before reaching the destination server.

## **Quick Revision**

- IPv4 = 32 bits = 4 octets.
    
- Each octet = 0–255.
    
- Subnet mask identifies network and host portions.
    
- `/24` = `255.255.255.0`.
    
- Private IP ranges: `10.x.x.x`, `172.16–31.x.x`, `192.168.x.x`.
    
- NAT allows private IP devices to access the Internet.
    
- Router forwards packets between networks.
# **TCP, UDP, Encapsulation & Packet Journey**

## **1. Transport Layer – TCP vs UDP**

Both TCP and UDP operate at **OSI Layer 4 (Transport Layer)**. They use port numbers to identify the sending and receiving applications.

|Feature|TCP|UDP|
|---|---|---|
|Full Name|Transmission Control Protocol|User Datagram Protocol|
|Connection|Connection-oriented|Connectionless|
|Reliability|Reliable delivery|No delivery guarantee|
|Acknowledgement|Yes|No|
|Speed|Generally slower|Generally faster|
|Example|Web browsing (HTTPS)|Online gaming, live streaming|

**Port numbers:**

- Identify applications or services running on a device.
    
- Range: `1–65535` (port 0 is reserved).
    

## **2. TCP Three-Way Handshake**

TCP establishes a connection before sending data using three steps:

SYN → SYN-ACK → ACK

1. **SYN:** Client requests a connection.
    
2. **SYN-ACK:** Server accepts and responds.
    
3. **ACK:** Client acknowledges the response.
    
After the handshake, data can be exchanged reliably.

## **3. Encapsulation**

**Encapsulation** is the process of adding headers (and sometimes trailers) to data as it moves down the network layers.

|Layer|Data Unit|
|---|---|
|Application|Data|
|Transport|TCP Segment / UDP Datagram|
|Internet|IP Packet|
|Link|Frame|

**Remember the order:**

```
Application Data
      ↓
TCP Segment / UDP Datagram
      ↓
IP Packet
      ↓
Data Link Frame
```

At the receiving device, the process is reversed. This is called **decapsulation**.

## **4. Life of a Packet**

Example: Searching for a room on TryHackMe.

1. Browser creates an HTTPS request.
    
2. TCP establishes a connection using the three-way handshake.
    
3. TCP divides the data into segments.
    
4. IP adds source and destination IP addresses.
    
5. Link Layer creates a frame and sends it to the router.
    
6. Routers forward the packet towards the destination server.
    
7. The server receives and processes the request.
    

## **5. Practical – Using Telnet**

**Telnet** allows us to connect to a remote system through a TCP port.

Although Telnet is insecure for remote administration because it sends data in cleartext, it is useful in this lab to test TCP services manually.

**Command format:**

```
telnet <target-IP> <port>
```

|Service|Port|Purpose|
|---|---|---|
|Echo|7|Returns the text you send|
|Daytime|13|Returns current date and time|
|HTTP|80|Serves web pages|

**Testing an HTTP server:**

```
telnet <target-IP> 80
```

Then enter:

```
GET / HTTP/1.1
Host: telnet.thm
```

- `GET /` requests the home page.
    
- `Host` identifies the requested website.
    
- `200 OK` means the HTTP request was successful.
    

**Exit Telnet:**

Press `Ctrl + ]`, then type:

```
quit
```

## **Quick Revision**

- **TCP:** Reliable, connection-oriented communication.
    
- **UDP:** Connectionless, no delivery guarantee.
    
- **TCP handshake:** SYN → SYN-ACK → ACK.
    
- **Port:** Identifies an application or service.
    
- **Encapsulation:** Adding headers/trailers as data moves down layers.
    
- **Decapsulation:** Removing them at the receiving device.
    
- **Telnet:** Useful for manually testing TCP services and ports.
# **DHCP and ARP**

## **1. DHCP (Dynamic Host Configuration Protocol)**

- DHCP automatically assigns network settings to devices when they connect to a network.
- It avoids manual configuration and IP address conflicts.
- DHCP uses **UDP**:
    - Server: Port `67`
    - Client: Port `68`
### **Network Settings Provided by DHCP**

- IP address
- Subnet mask
- Default gateway
- DNS server
### **DHCP Process – DORA**

Discover → Offer → Request → Acknowledge

1. **Discover:** Client broadcasts a request to find a DHCP server.
2. **Offer:** Server offers an available IP address
3. **Request:** Client requests the offered IP address
4. **Acknowledge:** Server confirms the IP address assignment.
**Important:** Before receiving an IP address, the client uses:

- Source IP: `0.0.0.0`
- Destination IP: `255.255.255.255`
- Destination MAC: `ff:ff:ff:ff:ff:ff`
## **2. ARP (Address Resolution Protocol)**

- ARP finds the **MAC address using an IP address**.
- It is used for communication within a local network.
### **How ARP Works**

1. **ARP Request:** Device broadcasts a message asking who owns a particular IP address.
2. **ARP Reply:** The device with that IP responds with its MAC address.
3. Devices can now communicate using MAC addresses.
### **Example**

```
Device A wants to communicate with Device B.
Device B IP: 192.168.66.1
ARP Request:
Who has 192.168.66.1?

ARP Reply:
192.168.66.1 is at 44:df:65:d8:fe:6c
```

### **Important ARP Details**

| Feature        | Value                    |
| -------------- | ------------------------ |
| Purpose        | IP address → MAC address |
| ARP Request    | Broadcast                |
| ARP Reply      | Usually Unicast          |
| Ethernet Type  | `0x0806`                 |
| Request Opcode | `1`                      |
| Reply Opcode   | `2`                      |

## **Quick Revision**

| DHCP                                   | ARP                                          |
| -------------------------------------- | -------------------------------------------- |
| Automatically assigns IP configuration | Finds MAC address using IP address           |
| Uses UDP ports 67 and 68               | Uses Ethernet frames                         |
| DORA process                           | Request and Reply                            |
| Helps devices join a network           | Helps devices communicate on a local network |

**Remember:**

- DHCP = Automatically gets an IP address.
- ARP = Finds the MAC address associated with an IP address.
# **ICMP, Traceroute & NAT**

## **1. ICMP (Internet Control Message Protocol)**

- Used for **network diagnostics and error reporting**.
    
- Two important commands use ICMP:
    

|Command|Purpose|
|---|---|
|`ping`|Checks connectivity and measures response time (RTT).|
|`traceroute` / `tracert`|Identifies the routers between your device and the destination.|

### **Ping**

- Sends an **ICMP Echo Request (Type 8)**.
    
- The target responds with an **ICMP Echo Reply (Type 0)**.
    
- Measures Round-Trip Time (RTT) and packet loss.
    

```
ping 192.168.1.1 -c 4
```

`-c 4` sends 4 packets.

### **Traceroute**

- Shows the path packets take to reach a destination.
    
- Uses **TTL (Time To Live)** to discover routers.
    
- When TTL reaches 0, the router drops the packet and sends an **ICMP Time Exceeded (Type 11)** message.
    

```
# Linux
traceroute example.com

# Windows
tracert example.com
```

## **2. Routing Protocols**

Routing protocols help routers find suitable paths for sending data.

|Protocol|Main Purpose|
|---|---|
|OSPF|Finds efficient paths using network topology information.|
|EIGRP|Cisco-developed routing protocol.|
|BGP|Exchanges routing information between networks on the Internet.|
|RIP|Selects routes based on the number of hops.|

## **3. NAT (Network Address Translation)**

- NAT allows multiple devices with **private IP addresses** to access the Internet using a single public IP address.
    
- It is usually performed by a router.
    
- The router maintains a translation table to track connections.
    

**Example:**

|Inside Network|Public Network|
|---|---|
|`192.168.0.129:15401`|`212.3.4.5:19273`|

The router translates the private IP address and port into a public IP address and port.

**PAT (Port Address Translation):**

- Allows multiple devices to share one public IP using different port numbers.
    
- Also called **NAT Overload**.
    
- Commonly used in home routers.
    

## **Quick Revision**

|Concept|Remember|
|---|---|
|ICMP|Network diagnostics and error reporting|
|Ping|Tests connectivity|
|Echo Request|ICMP Type 8|
|Echo Reply|ICMP Type 0|
|Traceroute|Discovers network path|
|TTL|Limits how many routers a packet can pass|
|Time Exceeded|ICMP Type 11|
|OSPF|Efficient routing using topology|
|EIGRP|Cisco-developed routing protocol|
|BGP|Routing between networks on the Internet|
|RIP|Routing based on hop count|
|NAT|Allows private devices to access the Internet through a public IP|
|PAT|Multiple devices share one public IP using ports|

# **DNS, HTTP/HTTPS, WHOIS & FTP**

## **1. DNS (Domain Name System)**

- DNS converts domain names into IP addresses.
    
- It operates at **Application Layer (Layer 7)**.
    
- Default port: `53` (UDP and TCP).
    

### **Important DNS Records**

|Record|Purpose|
|---|---|
|A|Maps domain to IPv4 address|
|AAAA|Maps domain to IPv6 address|
|CNAME|Maps one domain name to another|
|MX|Identifies the mail server for a domain|

### **Practical: Find an IP Address**

```
nslookup example.com
```

## **2. HTTP and HTTPS**

- **HTTP:** Protocol used by browsers to communicate with web servers.
    
- **HTTPS:** Secure version of HTTP.
    
- Both commonly use TCP.
    

|Protocol|Default Port|
|---|---|
|HTTP|80|
|HTTPS|443|

### **Important HTTP Methods**

|Method|Purpose|
|---|---|
|GET|Retrieve data|
|POST|Submit data|
|PUT|Create or update data|
|DELETE|Delete a resource|

### **Practical: Send an HTTP Request Using Telnet**

```
telnet <target-IP> 80
```

Then enter:

```
GET / HTTP/1.1
Host: telnet.thm
```

- `GET /` requests the home page.
    
- `Host` specifies the website.
    
- `200 OK` indicates a successful response.
    

## **3. WHOIS**

- WHOIS provides registration information about a domain.
    
- Can show registrar, creation date, expiry date and registrant details.
    
- Privacy protection can hide personal registration details.
    

### **Practical: Find Domain Information**

```
whois example.com
```

## **4. FTP (File Transfer Protocol)**

- FTP is used to transfer files between a client and a server.
    
- Uses TCP.
    
- Default control port: `21`.
    
- File transfers use a separate connection.
    

### **Important FTP Commands**

|Command|Purpose|
|---|---|
|USER|Enter username|
|PASS|Enter password|
|LIST|List available files|
|RETR|Download a file|
|STOR|Upload a file|
|QUIT|Close connection|

### **Practical: Connect to FTP Server and Download Files**

**Step 1: Connect to the FTP server**

```
ftp <target-IP>
```

**Step 2: Login**

```
Username: anonymous
Password: (press Enter if no password is required)
```

**Step 3: List available files**

```
ls
```

**Step 4: Download a file**

```
get coffee.txt
```

**Step 5: Exit FTP**

```
quit
```

### **TryHackMe Practical – Retrieve the Flag**

```
ftp 10.48.175.0
```

Then:

```
Name: anonymous
Password: (press Enter)

ls
get flag.txt
quit
```

The downloaded `flag.txt` file will be saved in your current local directory. Read it using:

```
cat flag.txt
```

## **Quick Revision**

|Protocol|Purpose|Default Port|
|---|---|---|
|DNS|Domain name to IP address|53|
|HTTP|Web communication|80|
|HTTPS|Secure web communication|443|
|WHOIS|Domain registration information|No single default port|
|FTP|File transfer|21 (control)|

**Remember:**

- DNS = Finds IP addresses using domain names.
    
- HTTP/HTTPS = Web communication.
    
- WHOIS = Domain registration details.
    
- FTP = Uploads and downloads files.
# **Email Protocols – SMTP, POP3 & IMAP**

## **1. SMTP (Simple Mail Transfer Protocol)**

- Used to **send emails** from a client to a mail server and between mail servers.
    
- Uses TCP.
    
- Default port: `25`.
    

### **Important SMTP Commands**

|Command|Purpose|
|---|---|
|`HELO` / `EHLO`|Start SMTP session|
|`MAIL FROM`|Specify sender|
|`RCPT TO`|Specify recipient|
|`DATA`|Start sending email content|
|`QUIT`|End session|

### **Practical: Send an Email Using Telnet**

**Step 1: Connect to SMTP server**

```
telnet <target-IP> 25
```

**Step 2: Enter SMTP commands**

```
HELO client.thm
MAIL FROM: <user@client.thm>
RCPT TO: <user@server.thm>
DATA
From: user@client.thm
To: user@server.thm
Subject: Test Email

Hello, this is a test email.
.
QUIT
```

**Remember:** A single dot (`.`) on a separate line indicates the end of the email.

## **2. POP3 (Post Office Protocol Version 3)**

- Used to **retrieve emails** from a mail server.
    
- Commonly downloads emails to a local device.
    
- Uses TCP port `110`.
    
- Basic POP3 retrieval may remove downloaded messages from the server.
    

### **Important POP3 Commands**

|Command|Purpose|
|---|---|
|`USER`|Enter username|
|`PASS`|Enter password|
|`STAT`|Show number and size of messages|
|`LIST`|List messages|
|`RETR`|Retrieve a message|
|`DELE`|Mark a message for deletion|
|`QUIT`|End session and apply changes|

### **Practical: Retrieve Emails Using Telnet**

**Step 1: Connect**

```
telnet <target-IP> 110
```

**Step 2: Login and retrieve email**

```
USER linda
PASS Pa$$123
STAT
LIST
RETR 1
QUIT
```

`RETR 1` retrieves the first email.

## **3. IMAP (Internet Message Access Protocol)**

- Used to access and synchronize emails across multiple devices.
    
- Emails remain stored on the server.
    
- Synchronizes read, moved and deleted messages.
    
- Uses TCP port `143`.
    

### **Important IMAP Commands**

|Command|Purpose|
|---|---|
|`LOGIN`|Authenticate user|
|`SELECT`|Select mailbox|
|`FETCH`|Retrieve email content|
|`MOVE`|Move messages|
|`COPY`|Copy messages|
|`LOGOUT`|End session|

### **Practical: Retrieve Emails Using Telnet**

**Step 1: Connect**

```
telnet <target-IP> 143
```

**Step 2: Login and retrieve email**

```
A LOGIN linda Pa$$123
B SELECT inbox
C FETCH 1 body[]
D LOGOUT
```

Note: IMAP commands require a tag before each command (`A`, `B`, `C`, `D` are examples).

## **4. SMTP vs POP3 vs IMAP**

|Protocol|Main Purpose|Default TCP Port|
|---|---|---|
|SMTP|Send emails|25|
|POP3|Retrieve emails|110|
|IMAP|Access and synchronize emails|143|

**Easy way to remember:**

- **SMTP** = Send emails.
    
- **POP3** = Download emails.
    
- **IMAP** = Synchronize emails across devices.
    

**Security note:** These default ports use unencrypted connections unless additional encryption is configured. Passwords and email contents may be exposed to someone capturing network traffic.

# **Network Security Protocols**

## **1. HTTP vs HTTPS**

- **HTTP:** Sends data in plain text. Attackers can read captured traffic.
    
- **HTTPS:** HTTP secured using TLS encryption.
    
- HTTPS protects data confidentiality and integrity.
    

### **HTTP vs HTTPS Communication**

|HTTP|HTTPS|
|---|---|
|TCP handshake|TCP handshake|
|HTTP communication|TLS handshake, then HTTP communication|
|Data is readable|Data is encrypted|
|Port 80|Port 443|

**HTTPS communication steps:**

1. TCP three-way handshake.
    
2. TLS session establishment.
    
3. Encrypted HTTP communication.
    

**Wireshark:** HTTP requests can be read directly, while HTTPS shows encrypted Application Data unless the traffic is decrypted using the required keys.

## **2. SSH (Secure Shell)**

- Used for secure remote access to another computer.
    
- Encrypts communication and protects against eavesdropping.
    
- Supports password and public-key authentication.
    
- Provides confidentiality, integrity and secure tunnelling.
    
- Supports X11 forwarding for remote graphical applications.
    

**Default port:** TCP `22`

### **Practical Commands**

Connect to a remote server:

```
ssh username@hostname
```

Connect with graphical application forwarding:

```
ssh -X username@hostname
```

## **3. Secure File Transfer**

|Protocol|Purpose|Default Port|
|---|---|---|
|SFTP|Secure file transfer using SSH|22|
|FTPS|FTP secured using TLS|990 (commonly)|
|FTP|Normal file transfer|21 (control)|

### **SFTP Practical Commands**

Connect:

```
sftp username@hostname
```

Download a file:

```
get filename
```

Upload a file:

```
put filename
```

**Remember:** SFTP and FTPS are different protocols.

## **4. TLS (Transport Layer Security)**

- TLS provides secure communication between clients and servers.
    
- Protects:
    
    - **Confidentiality:** Prevents others from reading data.
        
    - **Integrity:** Prevents undetected modification of data.
        
    
- HTTPS, SMTPS, POP3S and IMAPS use TLS for secure communication.
    
- TLS was developed as an upgrade to **SSL (Secure Sockets Layer)**.
    
- Current modern version covered in the lesson: TLS 1.3.
    

### **TLS Certificates**

Certificates help verify the identity of a server.

- **CA (Certificate Authority):** Trusted organisation that issues and signs certificates.
    
- **CSR (Certificate Signing Request):** Request submitted to a CA to obtain a certificate.
    
- **Self-signed certificate:** Signed by its own creator, not a trusted third-party CA. It should not be relied on to confirm server authenticity.
    
- **Let's Encrypt:** Provides free TLS certificates.
    

## **5. VPN (Virtual Private Network)**

- VPN creates an encrypted tunnel over the Internet.
    
- Allows remote users and branch offices to securely access a company's private network.
    
- Protects data from disclosure and alteration while travelling through the tunnel.
    

### **Main Uses**

- Connect remote offices to the main branch.
    
- Allow employees to access company resources remotely.
    
- Hide the user's public IP address behind the VPN server's public IP.
    
- Protect network traffic from being read by the local ISP.
    

**Example:** A company with offices in Colombo and Kandy can use a VPN to allow employees in both locations to access shared resources securely.

## **Quick Revision**

|Concept|Important Point|
|---|---|
|HTTP|Unencrypted web communication|
|HTTPS|HTTP secured using TLS|
|SSH|Secure remote access|
|SFTP|Secure file transfer over SSH|
|FTPS|FTP secured using TLS|
|TLS|Provides confidentiality and integrity|
|CA|Issues and signs digital certificates|
|Self-signed certificate|Not independently verified by a trusted CA|
|VPN|Creates an encrypted network tunnel|

## **TryHackMe – Important Answers**

1. **TLS upgraded and built upon:** SSL (Secure Sockets Layer).
    
2. **Certificate type not recommended for confirming server authenticity:** Self-signed certificate.
    
3. **Connect remote company offices securely:** VPN (Virtual Private Network).
    

_Note: The exact Wireshark packet numbers and number of TLS handshake packets are not included in the text you provided. You need the corresponding packet captures or screenshots to answer those accurately._