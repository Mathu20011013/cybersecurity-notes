# **Nmap – Network Scanning Notes**

## **1. Host Discovery – Find Live Hosts**

**Purpose:** Identify which devices are online in a network.

### **Target formats**

|Format|Example|Meaning|
|---|---|---|
|IP range (`-`)|`192.168.0.1-10`|Scan IPs from `.1` to `.10`|
|Subnet (`/`)|`192.168.0.1/24`|Scan the `/24` network|
|Hostname|`example.thm`|Scan using a hostname|

### **Important options**

|Option|Purpose|Example|
|---|---|---|
|`-sn`|Discover live hosts without scanning ports|`sudo nmap -sn 192.168.0.0/24`|
|`-sL`|List targets without scanning them|`nmap -sL 192.168.0.1/24`|

**How it works:**

- **Local network:** Nmap uses ARP requests to discover devices and can display their MAC addresses.
- **Remote network:** Nmap uses other discovery methods, such as ICMP and TCP probes, because routers separate the networks.

**Remember:**

- `-sn` = Find live hosts.
- `-sL` = List target IP addresses only.
- Run Nmap with `sudo` or root privileges for full scanning capabilities.

**Example question:**

For `192.168.0.1/27`, the last IP address is:

- `/27` = 32 IP addresses.
- Range = `192.168.0.0` to `192.168.0.31`.
- Last IP = `192.168.0.31`.
## **2. Port Scanning – Find Open Ports**

**Purpose:** Discover services listening on TCP and UDP ports.

There are 65,535 available TCP ports and 65,535 UDP ports.

### **TCP scanning**

|Option|Scan type|How it works|
|---|---|---|
|`-sT`|TCP Connect Scan|Completes the TCP three-way handshake|
|`-sS`|SYN Scan (Stealth)|Sends SYN and does not complete the handshake|

**Examples:**

```
sudo nmap -sT 192.168.1.10
```

Performs a TCP connect scan.

```
sudo nmap -sS 192.168.1.10
```

Performs a SYN scan.

**Difference:**

- `-sT`: Completes the connection and then closes it.
- `-sS`: Sends SYN; if the port is open, receives SYN-ACK and sends RST instead of completing the connection.

### **UDP scanning**

|Option|Purpose|Example|
|---|---|---|
|`-sU`|Scans UDP ports|`sudo nmap -sU 192.168.1.10`|

Common UDP services:

- DNS – Port 53
- DHCP – Ports 67 and 68
- NTP – Port 123
- SNMP – Port 161

### **Limiting port ranges**

|Option|Purpose|Example|
|---|---|---|
|Default|Scans 1,000 common ports|`nmap 192.168.1.10`|
|`-F`|Scans 100 common ports|`nmap -F 192.168.1.10`|
|`-p10-1024`|Scans ports 10–1024|`nmap -p10-1024 192.168.1.10`|
|`-p-25`|Scans ports 1–25|`nmap -p-25 192.168.1.10`|
|`-p-`|Scans all 65,535 ports|`nmap -p- 192.168.1.10`|
|`-p1-1023`|Scans well-known ports|`nmap -p1-1023 192.168.1.10`|

## **3. OS and Service Detection**

**Purpose:** Identify the target operating system and the services running on open ports.

### **Important options**

|Option|Purpose|Example|
|---|---|---|
|`-O`|Detect operating system|`sudo nmap -O 192.168.1.10`|
|`-sV`|Detect service names and versions|`sudo nmap -sV 192.168.1.10`|
|`-A`|Enables OS detection, version detection, traceroute and other features|`sudo nmap -A 192.168.1.10`|
|`-Pn`|Skip host discovery and treat targets as online|`sudo nmap -Pn 192.168.1.10`|

**Examples:**

```
sudo nmap -sS -O 192.168.1.10
```

Detects the operating system using a SYN scan.

```
sudo nmap -sS -sV 192.168.1.10
```

Finds open TCP ports and identifies their services and versions.

```
sudo nmap -Pn 192.168.1.10
```

Scans the target even if it does not respond to host discovery.

**Remember:**

- `-O` = Operating system.
- `-sV` = Service version.
- `-A` = Advanced detection.
- `-Pn` = Assume host is online.

## **4. Scan Timing and Speed**

**Purpose:** Control how fast Nmap performs a scan.

### **Timing templates**

|Option|Name|Speed|
|---|---|---|
|`-T0`|Paranoid|Very slow|
|`-T1`|Sneaky|Slow|
|`-T2`|Polite|Slower|
|`-T3`|Normal|Default|
|`-T4`|Aggressive|Fast|
|`-T5`|Insane|Very fast|

**Example:**

```
sudo nmap -T4 192.168.1.10
```

Uses aggressive timing.

You can also use the timing name:

```
sudo nmap -T aggressive 192.168.1.10
```

### **Other timing options**

|Option|Purpose|Example|
|---|---|---|
|`--min-parallelism`|Minimum parallel probes|`--min-parallelism 10`|
|`--max-parallelism`|Maximum parallel probes|`--max-parallelism 20`|
|`--min-rate`|Minimum packets per second|`--min-rate 100`|
|`--max-rate`|Maximum packets per second|`--max-rate 500`|
|`--host-timeout`|Maximum time to wait for a host|`--host-timeout 30s`|

**Remember:** Higher speed can create more network traffic and may increase the chance of detection or missed responses.

## **5. Verbosity and Debugging**

**Purpose:** Display more information while Nmap is scanning.

### **Options**

| Option | Purpose                 | Example                 |
| ------ | ----------------------- | ----------------------- |
| `-v`   | Verbose output          | `nmap -v 192.168.1.10`  |
| `-vv`  | More verbose output     | `nmap -vv 192.168.1.10` |
| `-v4`  | Verbosity level 4       | `nmap -v4 192.168.1.10` |
| `-d`   | Debugging output        | `nmap -d 192.168.1.10`  |
| `-d9`  | Maximum debugging level | `nmap -d9 192.168.1.10` |

**Remember:**

- `-v` = More scan progress information.
- `-d` = Detailed debugging information.
- Maximum debugging level = `-d9`.

## **6. Saving Nmap Scan Results**

**Purpose:** Save scan results into files for later analysis.
### **Output formats**

| Option | Format                  | Example                            |
| ------ | ----------------------- | ---------------------------------- |
| `-oN`  | Normal output           | `nmap -oN scan.txt 192.168.1.10`   |
| `-oX`  | XML output              | `nmap -oX scan.xml 192.168.1.10`   |
| `-oG`  | Grepable output         | `nmap -oG scan.gnmap 192.168.1.10` |
| `-oA`  | Saves all major formats | `nmap -oA scan 192.168.1.10`       |

**Example:**

```
sudo nmap -sS 192.168.1.10 -oA scan
```

Creates three files:
- `scan.nmap` – Normal output.
- `scan.xml` – XML output.
- `scan.gnmap` – Grepable output.    

## **7. Important Nmap Commands – Quick Revision**

| Command                  | Purpose                   |
| ------------------------ | ------------------------- |
| `nmap -sn <target>`      | Discover live hosts       |
| `nmap -sL <target>`      | List target IPs           |
| `nmap -sT <target>`      | TCP connect scan          |
| `nmap -sS <target>`      | TCP SYN scan              |
| `nmap -sU <target>`      | UDP scan                  |
| `nmap -p- <target>`      | Scan all ports            |
| `nmap -O <target>`       | OS detection              |
| `nmap -sV <target>`      | Service/version detection |
| `nmap -A <target>`       | Advanced scan             |
| `nmap -Pn <target>`      | Skip host discovery       |
| `nmap -T4 <target>`      | Aggressive timing         |
| `nmap -v <target>`       | Verbose output            |
| `nmap -d <target>`       | Debugging output          |
| `nmap -oA scan <target>` | Save all major formats    |

## **TryHackMe – Answers**

| Question                     | Answer          |
| ---------------------------- | --------------- |
| Last IP for `192.168.0.1/27` | `192.168.0.31`  |
| Option to enable debugging   | `-d`            |
| Name-based option for T4     | `-T aggressive` |

For the questions about the number of open TCP ports, the web server flag, and the server version on `10.48.161.52`, you need to run the scans in your AttackBox and inspect the results. Don't guess these values.

**Useful scan for the lab target:**

```
sudo nmap -sS -sV -O -p- 10.48.161.52
```

This scans all TCP ports and attempts to identify services, versions, and the operating system.