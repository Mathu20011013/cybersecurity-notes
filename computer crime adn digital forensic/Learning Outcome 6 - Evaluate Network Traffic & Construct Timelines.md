
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

