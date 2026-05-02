
Tool - Autopsy


When an investigator examines a suspect's hard drive, they need to:
1. **Understand the file system** — how data is organised, stored, and deleted
2. **Find relevant artifacts** — browser history, documents, emails, USB records
3. **Recover deleted data** — files the suspect tried to hide
4. **Build a timeline** — reconstruct what happened and when
5. **Interpret findings** — determine what the evidence means

#  **Part 1: File System Fundamentals**

## NTFS (New Technology File System) — Windows

Core Idea
- NTFS stores **file data + metadata**
- Key forensic value = **traces remain even after deletion**

### MFT (Master File Table)
- Every file/folder has an entry in NTFS
- Stores:
    - Name
    - Timestamps (MACE)
    - Size
    - Location
    - Permissions

 Forensics importance:
- Deleted files = MFT entry marked free (data often remains)
- File names + timestamps survive deletion
- Small files (< ~700B) = stored inside MFT (resident data)

MACE Timestamps

- **M** = Modified → content changed
- **A** = Accessed → file opened
- **C** = Created → file made on disk
- **E** = Entry Modified → metadata changed

 Forensics clue:
- Created > Modified → file was copied

###  ADS (Alternate Data Streams)

- Hidden data inside files
- Not visible in normal file listing
- Can store:
    - Hidden text
    - Metadata
    - Malware

👉 Example:  
`file.txt:hidden`

### $LogFile

- NTFS transaction log
- Records file system actions (create, delete, rename)
- Used for crash recovery
- Helps rebuild **event timeline**

### $UsnJrnl

- Change tracking journal
- Logs file/folder changes continuously:
    - Create
    - Modify
    - Rename
    - Delete

Very useful for:
- User activity tracking
- Malware/ransomware investigation

One-line memory summary
👉 NTFS keeps **3 layers of evidence:**
- MFT = file record
- ADS = hidden data
- Logs ($LogFile, $UsnJrnl) = activity history

 Exam shortcut memory
- MFT → “What file existed”
- ADS → “Hidden inside file”
- Logs → “What happened to file”

# FAT32 (File Allocation Table)

 Simple idea

FAT32 is a **basic and older file system** used in:

- USB drives
- SD cards
- Older systems

👉 It is **simple → easier to analyze, but less powerful**

##  Key structures

### File Allocation Table

- Acts like a **map**
- Tells which disk blocks (clusters) belong to a file

👉 Example:  
File A → Cluster 5 → Cluster 9 → Cluster 12

###  Directory Entries

- Store:
    - File name
    - Size
    - Timestamps
    - Starting location

👉 Think: “mini record of file"

 Data Area
- Where the **actual file content** is stored

## Forensic significance of FAT32
 Good for recovery
- When deleted:
    - Directory entry is marked deleted (not erased)
- Data often remains

👉 Easy to recover if not overwritten

 Limitations
- No journaling → no history tracking
- No permissions → no user control info
- No ADS → no hidden streams
- Less precise timestamps

## Key takeaway:

👉 FAT32 tells you:
- **What file existed**
- But NOT detailed history of what happened
## FAT32 vs NTFS (Core forensic idea)

In NTFS:
- NTFS = **rich evidence (logs + metadata)**
- FAT32 = **simple evidence (basic records only)**

| Feature | FAT32 | NTFS |
|---------|-------|------|
| Timestamps | Created, Modified, Accessed (less precise) | MACE (precise to 100ns) |
| Max File Size | 4 GB | 16 TB (theoretical) |
| Journaling | No | Yes ($LogFile, $UsnJrnl) |
| Alternate Data Streams | No | Yes |
| Permissions | No | Yes |
| Deleted File Recovery | Good (directory entry preserved) | Excellent (MFT entry preserved) |
#  ext4 (Linux File System)

ext4 is the **default Linux file system**
Used in:
- Linux systems
- Servers
- Android devices

## Key structures

###  Inodes
👉 Equivalent to MFT in NTFS
Stores:
- File metadata
- Permissions
- Timestamps
- Data pointers
###  Superblock
- Contains **overall file system info**
- Like:
    - size
    - structure
    - status

👉 Think: “file system blueprint”
###  Journal
- Records changes (like NTFS $LogFile)

👉 Helps:

- Crash recovery
- Forensic timeline analysis
### Directory Entries

- Map:
    - File name → inode
##  ext4 timestamps

- Created
- Modified
- Accessed
- Changed (metadata change)

👉 Very precise (nanoseconds)
##  Forensic significance of ext4

### Strong points

- Detailed metadata (via inodes)
- Journaling helps track changes
- Very precise timestamps

### 📌 Where it is used

- Linux servers (important in investigations)
- Android devices (mobile forensics)

# Part 2: File Deletion & Recovery (Short Notes)

## 1. What happens when a file is deleted?

### Step 1: Recycle Bin / Trash
- File is **not deleted**
- Just moved to Recycle Bin
- Easy restore
### Step 2: Recycle Bin emptied

- File system marks space as **free/available**
- In NTFS:
    - MFT entry = marked “not in use”
- In FAT32:
    - First character replaced (0xE5)

👉 **IMPORTANT:** Data still exists on disk

### Step 3: Overwriting

- New data replaces old data
- After overwrite → file is **gone permanently**

👉 **Deleted ≠ erased**  
Data remains until overwritten

#  2. Unallocated Space

- Free space not assigned to files
- May contain deleted file fragments
👉 Forensic tools scan this area for recovery
#  3. File Slack Space

Unused space inside a cluster

 Example:

- File size = 2,500 bytes
- Cluster size = 4,096 bytes
👉 Slack space = 1,596 bytes

✔ This slack may contain:
- Old deleted data fragments
## Types:

- RAM slack → leftover memory data
- Drive slack → unused disk space
# 🔍 4. Data Carving

Recover files WITHOUT file system info
### How it works:
- Scan raw disk for file signatures
### 📌 Examples:

- JPEG → `FF D8 FF`
- PDF → `%PDF`
- ZIP → `PK`
 Example:
Even if file is deleted:
- JPEG header found → file rebuilt

#  Final memory summary

- Delete → only marks space free
- Overwrite → permanent loss
- Unallocated space → hidden deleted data
- Slack space → leftover fragments
- Carving → rebuild files from signatures

# Part - 3  Windows Registry Forensics

## Core Idea

- Registry = **central database of Windows system + user activity**
- Stored in **hives**
- Very rich forensic evidence source
## Registry Root Hives

In HKEY_LOCAL_MACHINE:
- System-wide settings (hardware, software, services)
In HKEY_CURRENT_USER:
- Current user activity + preferences
Other hives:
- HKU → all users
- HKCR → file associations
- HKCC → hardware profile

## Registry Hive Files (Disk Level)

- SAM → user accounts + login info
- SECURITY → security policies
- SOFTWARE → installed programs
- SYSTEM → hardware + services
- NTUSER.DAT → user activity
- UsrClass.dat → shell settings
## Key Forensic Artifacts

- MRU (Recent Files)
	 Path: RecentDocs (HKCU)
	 Shows recently opened files
	 Works even if file is deleted
- USB History
	- - USBSTOR (HKLM\SYSTEM)
	- Shows:
	    - USB device name
	    - Serial number
	    - First & last connection
	👉 Used in data theft cases
- User Accounts (SAM)
	- Users, login times, password info
-  Installed Programs
	- Uninstall registry key
	- Shows installed software + install date
- Network History 
	- Wi-Fi networks connected
	- Helps locate device history
- Typed URLs
	- Manually typed browser URLs
	- Shows user intent browsing
- Startup Programs
	- Run / RunOnce keys
	- Used for persistence (malware hides here)
- Shutdown Time
	- - Last system shutdown time
	- Helps timeline building
- TimeZone Info
	- Converts timestamps correctly
	- Important for accurate timeline
	
- UserAssist
	- Programs run via Explorer
	- Stores run count + last execution
	- Data is ROT13 encode

**Registry** = **User activity + system configuration + forensic timeline evidence**

# Part 4 - Browser Forensics (Key Idea)

 Browsers store **user online activity locally**
Google Chrome stores:
- History → visited sites + time
- Cache → saved web pages
- Cookies → login/session data
- Downloads → files downloaded
- Passwords → saved logins
- Form data → typed searches
##  Browser data location (Chrome)
C:\Users\<user>\AppData\Local\Google\Chrome\User Data\Default\

##  Simple forensic example

- Visited: `gmail.com`
- Downloaded: `invoice.pdf`
- Searched: “how to bypass firewall”

 Shows user intent + activity timeline

# Part 5- Email Forensics (Key Idea)

Email evidence = **headers + local storage**
Microsoft Outlook stores emails in:

- PST / OST files → full mailbox (emails + attachments)
##  Malicious Email Example (Phishing)

From: security@apple-support.com  
To: user@gmail.com  
Subject: Your Apple ID is locked  
  
Received: from laptop-user (102.45.77.19)  
Received: from mail.fake-server.com (198.51.100.25)  
  
X-Originating-IP: 102.45.77.19  
Return-Path: fakehelp@scamdomain.com

##  Header Breakdown (Simple)

### 1. From (FAKE identity)
👉 Looks like Apple  
❌ Can be spoofed
✔ Purpose: trick user
### 2. Received (MOST IMPORTANT)
👉 Read bottom → top
- 102.45.77.19 = **attacker PC**
- 198.51.100.25 = **relay server**
✔ Purpose: shows real email path
### 3. X-Originating-IP
👉 102.45.77.19
✔ Confirms attacker device
### 4. Return-Path
👉 fakehelp@scamdomain.com
❌ Not Apple domain → phishing sign
##  Why this email is malicious
✔ Fake Apple identity  
✔ Real origin = attacker PC  
✔ Fake return domain  
✔ Designed to steal login credentials
# Part 6-  Timeline Forensics (Key Idea)

👉 Combine all timestamps to reconstruct events

Sources:
- File system timestamps
- Registry activity
- Browser history
- Email logs
- USB events
##  Simple example timeline
10:00 → User logs in  
10:05 → Opens email  
10:06 → Phishing email received  
10:07 → Clicked link  
10:08 → Malware downloaded  
10:10 → USB inserted  
10:15 → Files copied  
10:20 → System logout
##  Purpose
- Reconstruct attack story
- Find “what happened first → last”
- Detect suspicious patterns
# 🧠 SUPER SHORT MEMORY SUMMARY

👉 Browser = what user did online  
👉 Email = communication + attacker trace  
👉 Timeline = full story of attack