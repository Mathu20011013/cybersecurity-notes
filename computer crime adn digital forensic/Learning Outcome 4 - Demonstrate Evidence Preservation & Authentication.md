

## 1. Forensic Imaging

A **forensic image** is a **bit-by-bit exact copy** of a storage device (HDD, SSD, USB). It includes all data: active files, deleted files, hidden data, and free space.
###  Why not normal copy?
- Only copies visible files
- Misses deleted and hidden data
- Can change timestamps
###  Forensic image advantage:
- Complete and exact replica of disk
- Accepted in court
###  Image formats:
- **E01 (EnCase format)** → Most used in industry, supports compression + metadata
- **RAW / dd** → Simple bit-by-bit copy, no compression
- **AFF** → Open-source format
###  Example:
A suspect’s laptop HDD is imaged using **FTK Imager**, creating an **E01 file** instead of copying folders manually.
##  2. Hash Functions (Integrity Verification)
A **hash function** generates a **unique digital fingerprint** for data.
### Key properties:
- Same input → same hash
- Any change → completely different hash
- One-way (cannot reverse)
### Common algorithms:
- **MD5** → fast but weak
- **SHA-1** → outdated
- **SHA-256** → strong & widely used in forensics
### Purpose:
- To verify evidence is not modified
###  Example:
```
Original Drive SHA-256:  a3f2b8c9...Forensic Image SHA-256:  a3f2b8c9...Result: MATCH (evidence is authentic)
```
If values differ → evidence is **tampered ❌**

##  3. Write Blockers
A **write blocker** prevents any data from being written to a storage device during investigation.
### Why needed?
When a drive is connected:
- OS may change timestamps
- Temporary files may be written
- Evidence integrity can be damage
### Types:
####  Hardware Write Blocker
- Physical device between drive and computer
- Fully blocks write operations
- Industry standard
####  Software Write Blocker
- Software-based protection
- Less reliable than hardware
### Example:
A suspect USB drive is connected using a **Tableau hardware write blocker** before imaging in FTK Imager.
##  4. Chain of Custody
A **chain of custody** is a **documented record of everyone who handled evidence**.
### Purpose:
- Proves evidence was not tampered with
- Ensures legal admissibility
### Records include:
- Who collected evidence
- When and where it was collected
- Who accessed or transferred it
- Purpose of handling
###  Example flow:
1. Police officer collects laptop from crime scene
2. Transported to forensic lab
3. Analyst creates forensic image
4. Stored in evidence locker
5. Used in investigation

All steps are documented with timestamps and signatures.
##  5. Evidence Storage & Handling
### Physical storage:
- Locked evidence room
- Anti-static bags
- Controlled environment
### Digital storage:
- Forensic images stored securely
- Backup copies maintained
- Regular hash verification
### Rule:
 Never work on original evidence  
Always work on forensic copy

##  6. Legal Importance
To be accepted in court, evidence must follow legal rules:
###  Authentication (Rule 901)
- Prove evidence is real and unchanged
- Done using hashes + chain of custody
###  Expert Testimony (Rule 702)
- Use validated tools (FTK, Autopsy)
- Follow proper forensic procedures
###  Best Evidence Rule
- Court prefers original or exact verified copy

##  QUICK EXAMPLE CASE (Exam Friendly)
A suspect’s hard drive is seized:
1. Connected using **hardware write blocker**
2. Image created using **FTK Imager (E01 format)**
3. **SHA-256 hash** calculated for drive and image
4. Both hashes match → integrity confirmed
5. Evidence stored in **locked evidence locker**
6. Every step recorded in **chain of custody form**

 Result: Evidence is **legally valid and court-admissible**