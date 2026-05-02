
# Importance of Network Evidence 

1. **Exfiltration Detection**  
     Data theft always uses the network (uploads, email, FTP)
2. **Intrusion Analysis**  
     Attackers enter through the network; packets show their activity
3. **Communication Reconstruction**  
     Can rebuild emails, chats, and web activity from traffic
4. **Timeline Precision**  
     Network timestamps help verify system events
5. **Attribution**  
     IPs and domains help identify the source of the attack
# Part 1: Network Fundamentals for Forensics

## OSI MODEL 

Layer 7 , 4 , 3 are useful in for the forensics

Layer 7 - application layer
	- shows user activity and the content
	- email, web pages, DNS queries, file transfers
	- what was access or sent

Layer 6 -  presentation layer
	- Handles formatting and encryption 
	- SSL/TLS, encoding. compression
	- data maybe hidden here (encrypted)

		SSL/TLS - ensure 3 key things
			encryption
			authrntication
			Integrity
			
Layer 5 - session layer
	-  Manages start and end of connections
	-  login sessions, remote access sessions
	- when communication began and ended

Layer 4 - transport layer
	- control data delivery between devices
	- TCP/UDP, port numbers
	- how communication happen

Layer 3 - network layer
	- Identify the source and destination IPs 
	- routing between networks
	- who communicate with whom

Layer 2 - Data-link layer
	- local network identification 
	- Mac addresses, ARP mapping
	- Device identification inside LAN

Layer 1 -Physical layer
	- actual signal transmission
	- hardware level

### TCP (Transmission Control Protocol)
- **Connection-based communication** (must establish session first)
- Uses **3-way handshake (SYN → SYN-ACK → ACK)**
- **Reliable** → ensures data arrives in order and without loss
 **Forensics use:**
- Can rebuild full conversations from packet streams
- Shows complete user sessions (web browsing, file transfers)
###  UDP (User Datagram Protocol)
- **No connection setup**
- **Fast but unreliable** (no guarantee delivery or order)
 **Forensics use:**
- Shows individual requests/responses
- Useful for DNS queries, streaming, VoIP activity
###  HTTP / HTTPS (Web Traffic)
- **HTTP:** unencrypted → full data visible (URLs, forms, content)
- **HTTPS:** encrypted → only metadata visible (not content)
 **Forensics use:**
- Websites visited
- Upload/download activity
- User agent, cookies, request timing
### DNS (Domain Name System)
- Converts **domain names → IP addresses**
- Usually **unencrypted**
 **Forensics use:**
- Shows all domains a device tried to access
- Helps detect malicious or suspicious websites
- Often first indicator of compromise
###  SMTP / POP3 / IMAP (Email Protocols)
- **SMTP:** sends emails
- **POP3 / IMAP:** receives emails
 **Forensics use:**
- Email content (if unencrypted)
- Attachments
- Email headers (sender, recipient, route)
###  FTP (File Transfer Protocol)
- Used to **transfer files between systems**
- Usually **unencrypted**
 **Forensics use:**
- File uploads/downloads
- Username/password exposure
- Data exfiltration evidence
### SSH / RDP (Remote Access)
- **SSH:** secure remote terminal (Linux/Unix)
- **RDP:** remote desktop (Windows)
- Both are **encrypted**
 **Forensics use:**
- Connection logs (who accessed what system)
- Session time and duration
- Source and destination IPs
- Content not visible (due to encryption)
##  Quick Memory Summary

- **TCP → Full conversation reconstruction**
- **UDP → Quick single exchanges**
- **HTTP → Visible web activity**
- **HTTPS → Hidden content, visible metadata**
- **DNS → Website lookup history**
- **Email → Messages + headers**
- **FTP → File transfers + possible leaks**
- **SSH/RDP → Remote access sessions only**




# Part 2 - Packet Capture Analysis with Wireshark

Wireshark is the industry-standard network protocol analyser. It captures packets in real-time or reads saved PCAP files

PCAP - packet capture 

PCAP files contain raw network packets captured from network interface. This is the forensic images of the network traffic.

Sources of PCAP files:
- network monitoring systems (IDS/IPS)
- wireshark live capture
- tcpdump captures
- firewall/router logs
- network taps

## Wireshark interface

when open the PCAP file in Wireshark , we can see3 panes.
1. Packet list -  each line show one packet 
	- packet number
	- time stamp
	- source IP
	- destination IP
	- protocol
	- length
	- summary info
2. Packet detail - shows the selected packet details 
	- Frame - phyical layer
	- Ethernet - data link 
	- IP - network
	- TCP/UDP -transport
	- Application data (HTTP, DNS, etc.)
3. Packet bytes - raw hexadecimal/ascii representation


Wireshark display filters

1. By protocols  - tcp, udp, tcp, smtp
2. By IP address 
	- ip.addr == x.x.x. (traffic to/from this ip)
	- ip.src == x.x.x.x (traffic from this ip)
	- ip.dst == x.x.x.x (traffic to this Ip)
	- ip.addr == x.x.x.x/24 (traffic from/to this subnet)
3. By port  
	- tcp.port == 80  (http tafic)
4. By content 
	- http.request.uri contains "login" 
	- http.request.method == "POST" 
5. combination filters
	- ip.addr == 192.168.1.100 && http            # HTTP traffic from/to specific IP
	- dns && !dns.response                        # Only DNS queries (not responses)


Key Wireshark analysis

1. Follow tcp stream -  Right-click a packet → Follow → TCP Stream.

	- This reassembles the entire conversation between two endpoints, showing you the full communication in order.
	- Use case :
		Reading HTTP request/response content
		Viewing email messages (SMTP)
		Seeing FTP commands and responses
		Reconstructing any TCP-based communication

2. Protocol Hierarchy Statistics -  Statistics → Protocol Hierarchy. 
	- Shows a breakdown of all protocols in the capture.
	- Use cases:
		Quick overview of what types of traffic are present
		Identifying unusual protocols
		Spotting encrypted traffic (TLS/SSL percentages)

3. Conversations - Statistics → Conversations. 
	- Shows all unique communication pairs.
	- Use cases:
		Identifying who talked to whom
		Finding the most active connections
		Spotting unexpected external communications

4. DNS Analysis - Filter for `dns`

	- Use cases:
		See every domain the system tried to reach
		Identify connections to suspicious domains
		Detect DNS tunnelling (unusually long domain names or frequent queries)

5. Export Objects  -  File → Export Objects → HTTP (or other protocols).

	-  Extracts files transferred over the network.

	- Use cases:
		Recover downloaded files
		Extract uploaded documents
		Find malware payloads
		Reconstruct exfiltrated data

# Part 3: Suspicious Network Activity

IoCs - indicators of compromise 
IoCs  =  Clues that shows something bad happened  ( foot print of attacker/ evidence left behind in the network data)

**Iocs** 
1. connections to known bad IPs/Domains   (communicating with attackers)
	- device talking to hackers server
	- Found using DNS or IP logs
	-  often check with threat intelligence database
2. unusual outbound data (someone mightbe stealing the data)
	-  Too much data leaving the network
	- check conversation in  wireshark
	- sort by bytes sent 
3. unusual ports (hidden/malicious service running)
	- traffic on strange port , not commonly used port like 80,443
4. suspicious DNS queries (could be malware hiding data in dns)
	- weird/random domain names  (sjhbvjsh.example.com)
5. repeated fail connection ( port scanning, brute force)
	- many attempt but no success
6. Beaconing (Malware is “calling home” (Command & Control))
	- Device connects at **regular time intervals**
	- Every 60 seconds → same IP
7. Large post request (Possible file upload or data theft)
	- Big uploads using HTTP POST
8. Cleartext credentials ( attackers can steal credentials)
	- Passwords sent without encryption - found in HTTP,FTP

**common attack patterns**

1. Port Scan ( “Attacker is searching for open doors”)
	Attacker checks many ports on a system
	What you see:
	- Many SYN packets
	- No proper connection


2. Brute Force Attack (“Trying to guess password”)
	 Trying many passwords
	What you see:
	- Many login attempts (SSH, FTP, etc.)
	- Fast repeated connections

3. Data Exfiltration ( “Data is being stolen”)
	 Stealing data from system
	What you see:
	- Large uploads
	- External IP connections

4.  DNS Tunneling (“Data hidden in DNS traffic”)
	 Hiding data inside DNS requests
	What you see:
	- Very long domain names
	- Strange DNS patterns

5. Command & Control (C2) ( “Infected system is being controlled”)
	 Malware controlled remotely
	What you see:
	- Regular connections (like every 30–60 sec)
	- Same IP repeatedly


# Part 4: Advanced Timeline Construction

Timeline construction is the process of combining evidence from multiple digital sources into a single chronological sequence to understand what happened during an incident. 

It helps rebuild the full sequence of user and attacker activity.

Timeline data sources include:

- **File system (MFT):** file creation, modification, and access times
- **Windows Registry**: system and user activity changes
- **Event Logs:** logins, service starts, system events
- **Network captures:** connections, DNS queries, data transfers
- **Browser history**: visited websites with timestamps
- **Prefetch, LNK, Jump Lists:** program execution and file access history
- **USB logs:** device connection and disconnection times

**Super timeline:**

- Combines all evidence sources into one unified timeline
- Created using tools like log2timeline
- Produces a large dataset that is filtered for analysis

**Timeline analysis steps:**

- Identify the time range of the incident
- Filter relevant time period data
- Identify anchor events (e.g., login, file creation, network connection)
- Expand analysis before and after anchor events
- Correlate evidence across different sources
- Build a clear chronological narrative

Example:

- 14:29: file update.exe created in temp folder
- 14:30: DNS query to suspicious domain and execution of update.exe
- 14:30:17: network upload of 2.3 MB to external server
- 14:35: second network connection downloads data
- Correlation of file, registry, and network evidence shows malware execution, persistence, and data exfiltration

# Part 5: Event Log Analysis

Windows Event Logs are one of the most important sources in digital forensics because they record **system activity with exact timestamps**. 

Unlike file system artifacts, event logs directly show **what the system and users did and when they did it**.


## Key Event Log Files (What they are used for)

- Security.evtx → Tracks security-related events such as logins, failed logins, and access attempts
- System.evtx → Tracks system-level events like service starts, shutdowns, and driver loading
- Application.evtx → Tracks application errors, installations, and software activity
- PowerShell/Operational.evtx → Records PowerShell command execution (important for attackers)
- TaskScheduler/Operational.evtx → Shows scheduled task creation and execution (often used for persistence)

 Simple idea: Each log file records a different type of system behavior.

## Critical Event IDs (Most Important for Exams)

- 4624 → Successful login (who logged in, when, where from)
- 4625 → Failed login attempts (brute force or password guessing)
- 4634 → Logoff (session ended)
- 4648 → Login using explicit credentials (often lateral movement)
- 4672 → Admin privileges assigned (high privilege access)
- 4688 → Process creation (what programs were executed)
- 4697 / 7045 → Service installed (possible malware persistence)
- 4720 → New user account created (backdoor account)
- 4732 → User added to admin group (privilege escalation)
- 1102 → Audit logs cleared (anti-forensics activity)

Simple idea: Event IDs are **codes that tell exactly what happened in the system**

## Logon Types (Very Important Concept)

Event 4624 includes a logon type which explains how the user logged in:

- Type 2 → Local login at the machine
- Type 3 → Network access (shared folders, remote access)
- Type 4 → Batch job or scheduled task
- Type 5 → Service account login
- Type 7 → Unlock workstation
- Type 10 → Remote Desktop login (RDP)
- Type 11 → Cached login (offline login)

## Forensic Meaning (How to interpret)

- Logon Type 10 from unknown IP → possible attacker using RDP
- Logon Type 3 accessing many systems → possible lateral movement
- Event 1102 → attacker trying to hide actions by clearing logs
- Event 4688 showing unknown process → possible malware execution