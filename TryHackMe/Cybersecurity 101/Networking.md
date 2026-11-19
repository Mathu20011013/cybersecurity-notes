
# **OSI Model (Open Systems Interconnection)**

## **1. What is the OSI Model?**

The **OSI Model** is a networking model developed by the International Organization for Standardization (ISO). It explains how data travels between devices over a network.

It divides network communication into **7 layers**, with each layer performing a specific task.

**Simple example:** When you open a website, several networking processes work together to send your request from your computer to the web server and return the webpage.

## **2. The Seven Layers of the OSI Model**

[Data Manipulation Tasks Using KNIME for ETL (Extract–Transform–Load) Processes | by Mohamad Mahmood | Low Code for Data Science | Medium](https://images.openai.com/static-rsc-4/Ndx1HHIodxb7en6l3H5zwKijLaWHtyjZ0BSgGdR_VZZN-VraPCFzxzgfmGSQftTt_4Gqe_5MK2OZ9NgcXJS1XdTlBq-WYbUUVr-6epIIl2SWHuAYA8l13Wt2jFN5iMVR_lg4MBhaT3s4B6zCzV30a4Ir3HWDffyEgdkfQ0H9ap4?purpose=inline)

[medium.com](https://medium.com/low-code-for-advanced-data-science/data-manipulation-tasks-using-knime-for-etl-extract-transform-load-processes-4a6d0ecb772b?utm_source=chatgpt.com)

Mnemonic to remember the layers from bottom to top:

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
