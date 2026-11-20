
# **Tcpdump – Packet Capture and Analysis**

## **1. What is Tcpdump?**

- `tcpdump` is a command-line tool used to capture and analyse network packets.
- Useful for network troubleshooting and security analysis.
- Requires `sudo` or root privileges to capture live traffic.
- Can also read previously saved `.pcap` files.

## **2. Basic Tcpdump Options**

|Option|Purpose|Example|
|---|---|---|
|`-i`|Select network interface|`tcpdump -i eth0`|
|`-w`|Save captured packets to a file|`tcpdump -w traffic.pcap`|
|`-r`|Read packets from a file|`tcpdump -r traffic.pcap`|
|`-c`|Capture a specific number of packets|`tcpdump -c 10`|
|`-n`|Display IP addresses in numeric format|`tcpdump -n`|
|`-nn`|Disable IP and port name resolution|`tcpdump -nn`|
|`-v`|Display more packet details|`tcpdump -v`|
|`-vv` / `-vvv`|Display increasingly detailed output|`tcpdump -vv`|

### **Examples**

```
# Show available network interfaces
ip a

# Capture packets on all interfaces
sudo tcpdump -i any

# Capture 10 packets
sudo tcpdump -i eth0 -c 10

# Save packets to a file
sudo tcpdump -i eth0 -w traffic.pcap

# Read a saved capture
tcpdump -r traffic.pcap -n
```

## **3. Filtering Expressions**

Filtering helps capture or display only the packets you need.

|Filter|Purpose|Example|
|---|---|---|
|`host IP`|Traffic to or from a host|`host 192.168.1.10`|
|`src host IP`|Traffic from a specific host|`src host 192.168.1.10`|
|`dst host IP`|Traffic to a specific host|`dst host 192.168.1.10`|
|`port PORT`|Traffic using a port|`port 53`|
|`src port PORT`|Traffic from a source port|`src port 443`|
|`dst port PORT`|Traffic to a destination port|`dst port 80`|
|`tcp`|TCP traffic|`tcp`|
|`udp`|UDP traffic|`udp`|
|`icmp`|ICMP traffic|`icmp`|
|`arp`|ARP packets|`arp`|
|`ip`|IPv4 packets|`ip`|
|`ip6`|IPv6 packets|`ip6`|

### **Examples**

```
# Capture traffic from a specific IP
sudo tcpdump host 192.168.1.10 -n

# Capture traffic to a specific IP
sudo tcpdump dst host 192.168.1.10 -n

# Capture DNS traffic
sudo tcpdump port 53 -n

# Capture SSH traffic
sudo tcpdump tcp port 22 -n

# Capture ICMP traffic
sudo tcpdump icmp -n

# Read only ARP packets from a file
tcpdump -r traffic.pcap -n arp
```

## **4. Logical Operators**

|Operator|Purpose|Example|
|---|---|---|
|`and`|Both conditions must match|`host 1.1.1.1 and tcp`|
|`or`|Either condition can match|`udp or icmp`|
|`not`|Excludes a condition|`not tcp`|

### **Example**

```
# TCP traffic involving a specific host
sudo tcpdump host 1.1.1.1 and tcp -n

# Capture UDP or ICMP traffic
sudo tcpdump udp or icmp -n

# Capture everything except TCP
sudo tcpdump not tcp -n
```

## **5. Advanced Filtering**

### **Packet Length**

|Filter|Purpose|Example|
|---|---|---|
|`greater LENGTH`|Packets equal to or larger than the specified length|`greater 1500`|
|`less LENGTH`|Packets equal to or smaller than the specified length|`less 60`|

```
# Packets 15000 bytes or larger
tcpdump -r traffic.pcap -n greater 15000

# Packets 60 bytes or smaller
tcpdump -r traffic.pcap -n less 60
```

### **Filtering TCP Flags**

TCP flags help identify different stages of TCP communication.

|Flag|Meaning|
|---|---|
|`tcp-syn`|Starts a TCP connection|
|`tcp-ack`|Acknowledges received data|
|`tcp-fin`|Finishes a connection|
|`tcp-rst`|Resets a connection|
|`tcp-push`|Pushes data to the receiving application|

**Important filters:**

```
# Only SYN flag is set
tcpdump "tcp[tcpflags] == tcp-syn"

# SYN flag is present (other flags may also be set)
tcpdump "tcp[tcpflags] & tcp-syn != 0"

# SYN or ACK flag is present
tcpdump "tcp[tcpflags] & (tcp-syn|tcp-ack) != 0"
```

## **6. Displaying Captured Packets**

|Option|Purpose|Example|
|---|---|---|
|`-q`|Brief packet information|`tcpdump -r traffic.pcap -q`|
|`-e`|Display Ethernet header and MAC addresses|`tcpdump -r traffic.pcap -e`|
|`-A`|Display packet data as ASCII|`tcpdump -r traffic.pcap -A`|
|`-xx`|Display packet data in hexadecimal|`tcpdump -r traffic.pcap -xx`|
|`-X`|Display packet data in hexadecimal and ASCII|`tcpdump -r traffic.pcap -X`|

### **Examples**

```
# Display MAC addresses
tcpdump -r traffic.pcap -e

# Display readable ASCII data
tcpdump -r traffic.pcap -A

# Display hexadecimal data
tcpdump -r traffic.pcap -xx

# Display both hexadecimal and ASCII
tcpdump -r traffic.pcap -X
```

## **7. Useful Practical Commands**

|Task|Command|
|---|---|
|View first 5 packets|`tcpdump -r traffic.pcap -c 5 -n`|
|Find traffic from an IP|`tcpdump -r traffic.pcap src host 192.168.124.1 -n`|
|Find traffic to an IP|`tcpdump -r traffic.pcap dst host 192.168.124.1 -n`|
|Find DNS packets|`tcpdump -r traffic.pcap port 53 -n`|
|Find ARP packets|`tcpdump -r traffic.pcap -n -e arp`|
|Count packets from an IP|`tcpdump -r traffic.pcap src host 192.168.124.1 -n \\| wc -l`|

## **8. Practical – Find an ARP Request**

**TryHackMe task:** Find the MAC address of the host that sent the ARP request asking for `192.168.124.137`.

**Step 1: Read the capture and display ARP packets with MAC addresses.**

```
tcpdump -r traffic.pcap -n -e arp
```

**Step 2: Identify the ARP request.**

Look for a line similar to:

```
ARP, Request who-has 192.168.124.137 tell 192.168.124.X
```

**Step 3: Find the sender's MAC address.**

Example:

```
aa:bb:cc:11:22:33 > ff:ff:ff:ff:ff:ff
ARP, Request who-has 192.168.124.137
```

The sender's MAC address is:

```
aa:bb:cc:11:22:33
```

Example MAC address only. Use the actual source MAC address from your packet capture for the answer.

## **Quick Revision**

- `-i` = Select interface.
- `-w` = Save capture.
- `-r` = Read capture.
- `-c` = Packet count.
- `-n` = Numeric IP addresses.
- `-nn` = Numeric IP addresses and ports.
- `host` = Filter by host.
- `port` = Filter by port.
- `arp`, `tcp`, `udp`, `icmp` = Protocol filters.
- `and`, `or`, `not` = Combine filters.
- `-e` = Show MAC addresses.
- `-A` = ASCII output.
- `-xx` = Hexadecimal output.
- `-X` = Hexadecimal + ASCII.

**SOC Analyst tip:** Practise combining `-r`, `-n`, `-e` and filtering expressions. These are especially useful when investigating saved PCAP files.