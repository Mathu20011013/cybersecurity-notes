# 1. Introduction

## What is Linux?

**Definition**
- Linux is a free and open-source operating system.
- It manages computer hardware and software resources.
- It allows users to run applications and manage files.

**Why Linux is Important**
- Free to use and modify.
- Stable and reliable.
- Highly secure.
- Widely used in servers and cloud environments.
- Supports many programming languages and tools.

**Why Cybersecurity Professionals Use Linux**
- Most security tools are built for Linux.
- Easy to automate tasks using the command line.
- Commonly used for penetration testing and digital forensics.
- Many web servers and cloud systems run Linux.
- Provides detailed system and log management.

## Why Learn Linux?

### Server Administration
- Manage Linux servers.
- Configure services and users.
- Monitor system performance.

### Cloud Computing
- Most cloud servers use Linux.
- Used in AWS, Azure, and Google Cloud.
- Helps manage virtual machines and containers.

### Penetration Testing
- Used to test system security.
- Supports tools like Nmap, Metasploit, and Burp Suite.
- Common operating system for ethical hackers.

### Digital Forensics
- Analyze files and system logs.
- Recover and investigate evidence.
- Examine compromised systems.

### Security Operations Center (SOC)
- Monitor security logs.
- Investigate suspicious activities.
- Analyze running processes and network connections.
- Respond to security incidents.


# 2. Linux Basics

## Linux Distributions

A Linux distribution (distro) is a version of Linux that includes the Linux kernel, software, and tools.

### Ubuntu
- Beginner-friendly.
- Popular for desktops and servers.
- Large community support.

### Kali Linux
- Designed for cybersecurity professionals.
- Includes many penetration testing tools.
- Commonly used in ethical hacking.

### Debian
- Stable and reliable.
- Used for servers.
- Parent distribution of Ubuntu.

### CentOS
- Enterprise Linux distribution.
- Known for stability.
- Commonly used in business environments.
- *(Note: Newer systems mainly use CentOS Stream or alternatives like Rocky Linux and AlmaLinux.)*

### Fedora
- Latest Linux technologies.
- Frequently updated.
- Good for developers and testing.


## Linux Architecture

Linux consists of four main components:

### Kernel
- Core of the operating system.
- Manages hardware resources.
- Controls CPU, memory, and devices.

### Shell
- Interface between the user and the kernel.
- Accepts and executes commands.
- Example: Bash.

### File System
- Organizes files and directories.
- Stores user and system data.
- Starts from the root directory (`/`).

### User Applications
- Programs used by users.
- Examples:
  - Firefox
  - VS Code
  - Nmap
  - Wireshark


# 3. Linux File System

## What is the Linux File System?

- The Linux file system organizes all files and directories.
- Everything in Linux starts from the **root directory (`/`)**.
- Files, folders, devices, and storage are organized under the root directory.

### Simple Linux File System Structure

```text
/
├── home
├── root
├── etc
├── var
├── tmp
├── usr
├── bin
└── opt
```

> ** Remember:** In Linux, **everything starts from the root directory (`/`)**.


|Directory|Purpose|Common Files/Contents|Why It Matters|
|---|---|---|---|
|**`/`**|Root directory of the Linux file system.|Contains directories like `/home`, `/etc`, `/var`, `/usr`.|Every file and directory starts from here.|
|**`/home`**|Stores personal files of normal users.|Documents, Downloads, Pictures, Desktop files.|Users keep their personal files here.|
|**`/root`**|Home directory of the root (administrator) user.|Admin scripts, configuration files.|Used only by the root user for system administration.|
|**`/etc`**|Stores system configuration files.|`passwd`, `shadow`, `hosts`, SSH configuration.|Important for configuring and managing the system.|
|**`/var`**|Stores files that change frequently.|Log files, cache, mail files, temporary databases.|Useful for troubleshooting and security investigations.|
|**`/tmp`**|Stores temporary files.|Temporary application and installation files.|Files may be deleted after a reboot.|
|**`/usr`**|Stores installed software and shared resources.|Applications, libraries, documentation.|Contains most installed programs in Linux.|
|**`/bin`**|Stores essential system commands.|`ls`, `cp`, `mv`, `rm`, `cat`, `pwd`.|Required for basic Linux operations.|
|**`/opt`**|Stores optional or third-party software.|Google Chrome, VMware, custom applications.|Keeps additional software separate from system files.|



##  Linux File System for SOC Analysts

| Directory | SOC Use Case |
|-----------|--------------|
| `/var/log` | Investigate security logs and incidents |
| `/etc` | Check configuration changes and user settings |
| `/home` | Look for suspicious user files or scripts |
| `/tmp` | Search for malware or temporary malicious files |
| `/bin` | Verify important system commands |
| `/opt` | Check third-party applications for vulnerabilities |

##  Remember

- Every path starts from the **root directory (`/`)**.
- `/home` is for **normal users**.
- `/root` is for the **administrator**.
- `/etc` stores **configuration files**.
- `/var/log` contains **system logs**.
- `/tmp` stores **temporary files**.
- `/bin` contains **essential Linux commands**.
- `/usr` stores **installed software**.
- `/opt` stores **optional applications**.


# 4. Working with Files and Directories

## 4.1 Connecting to a Linux System (SSH)

### What is SSH?

- SSH stands for **Secure Shell**.
- It is a secure protocol used to connect to another computer over a network.
- SSH encrypts communication between the client and the server.

### Why Use SSH?

- Access a Linux server remotely.
- Manage servers without being physically present.
- Execute Linux commands securely.
- Transfer files securely (using SCP or SFTP).
### Why is SSH Important in Cybersecurity?

- SOC analysts use SSH to investigate Linux servers.
- Administrators manage servers remotely.
- Incident responders collect logs and analyze systems through SSH.
- Cloud servers (AWS, Azure, GCP) are commonly accessed using SSH.

### Basic SSH Syntax

```
ssh username@ip_address
```

Example

```
ssh ubuntu@192.168.1.10
```


### Example Output

```
ubuntu@server:~$
```

You are now connected to the remote Linux server.


### Remember

- SSH uses **Port 22** by default.
- SSH communication is encrypted.
- Never share your private SSH key.

### 4.2 File and Directory Commands

Use **one table** for all the basic commands.

|Command|Purpose|Example|Why It Is Useful|
|---|---|---|---|
|`pwd`|Shows the current working directory.|`pwd`|Check your current location in the file system.|
|`ls`|Lists files and directories.|`ls -l`|View the contents of a directory.|
|`cd`|Changes the current directory.|`cd Documents`|Navigate between directories.|
|`mkdir`|Creates a new directory.|`mkdir Projects`|Organize files into folders.|
|`rmdir`|Removes an empty directory.|`rmdir Test`|Delete unused empty folders.|
|`touch`|Creates a new empty file.|`touch notes.txt`|Create files quickly.|
|`cp`|Copies files or directories.|`cp file.txt backup.txt`|Create backups or duplicate files.|
|`mv`|Moves or renames files.|`mv file.txt Documents/`|Organize or rename files.|
|`rm`|Removes files or directories.|`rm file.txt`|Delete unwanted files.|
|`cat`|Displays file contents.|`cat notes.txt`|View small text files.|
|`less`|Opens large files one page at a time.|`less access.log`|Read large log files easily.|
|`head`|Displays the first lines of a file.|`head access.log`|Quickly inspect the beginning of a file.|
|`tail`|Displays the last lines of a file.|`tail access.log`|View recent log entries.|

### Then add a few important commands separately

Instead of making **all commands** separate, only give detailed explanations for the **important ones**.

For example:
## `find`
### Purpose
Searches for files and directories.
### Syntax

```
find [location] -name filename
```

### Examples

```
find -name passwords.txt
find -name "*.txt"
```

### Common Options

|Option|Description|
|---|---|
|`-name`|Search by file name|
|`-type f`|Search only files|
|`-type d`|Search only directories|

### SOC Use Case

- Find suspicious files.
- Locate configuration files.
- Search for malware.
## `grep`

Do the same because it's very important for SOC.

### 4.3 Searching Files

|Command|Purpose|Common Example|
|---|---|---|
|`find`|Search for files|`find -name "*.txt"`|
|`grep`|Search text inside files|`grep "ERROR" log.txt`|
|`grep -R`|Search recursively|`grep -R "root" /etc`|

### 4.4 Shell Operators

A table is perfect here too.

|Operator|Purpose|Example|Notes|
|---|---|---|---|
|`&`|Run a command in the background|`python3 app.py &`|Terminal remains usable.|
|`&&`|Run the next command only if the first succeeds|`mkdir Test && cd Test`|Stops if the first command fails.|
|`>`|Redirect output to a file (overwrite)|`echo "Hello" > notes.txt`|Existing content is replaced.|
|`>>`|Append output to a file|`echo "World" >> notes.txt`|Existing content is preserved.|


# 5. File Permissions

## What Are File Permissions?

- Linux controls who can access each file and directory.
- Permissions help protect files from unauthorized access or changes.
- Permissions can be viewed using:

```bash
ls -l
```
### Example

```text
-rw-r--r-- 1 mathu students 120 Jul 30 10:30 notes.txt
```

The important section is:

```text
-rw-r--r--
```

## Understanding the Permission Structure

```text
-   rw-   r--   r--
│    │     │     │
│    │     │     └── Others
│    │     └──────── Group
│    └────────────── Owner
└─────────────────── File type
```

|Section|Meaning|
|---|---|
|First character|File type|
|First three permissions|Owner permissions|
|Next three permissions|Group permissions|
|Last three permissions|Others’ permissions|

## File Type

The first character shows the type of item.

|Symbol|Meaning|
|---|---|
|`-`|Regular file|
|`d`|Directory|
|`l`|Symbolic link|

### Examples

```text
-rw-r--r--   Regular file
drwxr-xr-x   Directory
lrwxrwxrwx   Symbolic link
```

## Permission Types
Linux uses three main permissions:

|Permission|Symbol|Numeric value|Meaning for a File|Meaning for a Directory|
|---|--:|--:|---|---|
|Read|`r`|`4`|View the file contents|List files inside the directory|
|Write|`w`|`2`|Edit or change the file|Create, delete or rename items inside|
|Execute|`x`|`1`|Run the file as a program or script|Enter and access the directory|


## Read Permission — `r`

### For a File
- Allows the user to view the contents.
- Example:

```bash
cat notes.txt
```
### For a Directory

- Allows the user to list its contents.
- Example:

```bash
ls Documents
```
## Write Permission — `w`

### For a File

- Allows the user to modify the file.
- Allows content to be added or removed

### For a Directory

- Allows the user to create, delete or rename files inside it.


> [!NOTE]  
> Directory write permission controls changes inside the directory, not just changes to the directory itself.

## Execute Permission — `x`

### For a File

- Allows the file to run as a program or script.

Example:

```bash
./script.sh
```

### For a Directory

- Allows the user to enter the directory.

Example:

```bash
cd Projects
```


## Owner, Group and Others

Linux permissions are assigned to three categories.

|Category|Meaning|
|---|---|
|Owner|The user who owns the file|
|Group|Users who belong to the file’s group|
|Others|Every other user on the system|

### Example

```text
-rwxr-x---
```

Breakdown:

|Category|Permission|Meaning|
|---|---|---|
|Owner|`rwx`|Read, write and execute|
|Group|`r-x`|Read and execute|
|Others|`---`|No permission|


## File Owner and Group

Use `ls -l` to view the owner and group.

```bash
ls -l notes.txt
```

Example output:

```text
-rw-r----- 1 mathu students 120 Jul 30 10:30 notes.txt
```

|Part|Value|
|---|---|
|Owner|`mathu`|
|Group|`students`|
|Permissions|`rw-r-----`|

This means:

- `mathu` can read and write.
- Members of `students` can read.
- Other users have no access.

## Numeric Permissions

Permissions can also be represented using numbers.

|Permission|Value|
|---|--:|
|Read `r`|`4`|
|Write `w`|`2`|
|Execute `x`|`1`|
|No permission `-`|`0`|

The values are added for each category.

## Permission Calculations

|Permissions|Calculation|Value|
|---|--:|--:|
|`---`|0|0|
|`--x`|1|1|
|`-w-`|2|2|
|`-wx`|2 + 1|3|
|`r--`|4|4|
|`r-x`|4 + 1|5|
|`rw-`|4 + 2|6|
|`rwx`|4 + 2 + 1|7|

## Example: `rwxr-xr-x`

```text
rwx   r-x   r-x
 │     │     │
 7     5     5
```

|Category|Permissions|Calculation|Value|
|---|---|--:|--:|
|Owner|`rwx`|4 + 2 + 1|7|
|Group|`r-x`|4 + 1|5|
|Others|`r-x`|4 + 1|5|

Therefore:

```text
rwxr-xr-x = 755
```

## Common Permission Values

|Numeric|Symbolic|Meaning|
|--:|---|---|
|`777`|`rwxrwxrwx`|Everyone has full access|
|`755`|`rwxr-xr-x`|Owner has full access; others can read and execute|
|`750`|`rwxr-x---`|Owner has full access; group can read and execute; others have no access|
|`700`|`rwx------`|Only the owner has access|
|`644`|`rw-r--r--`|Owner can read and write; others can only read|
|`600`|`rw-------`|Only the owner can read and write|

> [!WARNING]  
> Avoid using `777` unless it is genuinely necessary. It allows every user to read, modify and execute the file.

## Changing Permissions with `chmod`

## Purpose

- `chmod` means **change mode**.
- It changes file or directory permissions.
## Numeric Syntax

```bash
chmod permission file_name
```

### Example

```bash
chmod 750 system_overview.txt
```

Meaning:

|Category|Value|Permission|
|---|--:|---|
|Owner|7|Read, write and execute|
|Group|5|Read and execute|
|Others|0|No access|

## More `chmod` Examples

```bash
chmod 755 script.sh
```

- Owner: read, write and execute.
- Group: read and execute.
- Others: read and execute.

```bash
chmod 600 private.txt
```

- Only the owner can read and write.
- Group and others have no access.

```bash
chmod 644 report.txt
```

- Owner can read and write.
- Group and others can only read.
## Symbolic `chmod`

Permissions can also be changed using letters.

|Symbol|Meaning|
|---|---|
|`u`|User or owner|
|`g`|Group|
|`o`|Others|
|`a`|All users|
|`+`|Add permission|
|`-`|Remove permission|
|`=`|Set exact permission|

### Examples

Add execute permission for the owner:

```bash
chmod u+x script.sh
```

Remove write permission from the group:

```bash
chmod g-w report.txt
```

Give others read permission:

```bash
chmod o+r report.txt
```

Remove execute permission from everyone:

```bash
chmod a-x script.sh
```
## Changing Ownership with `chown`

## Purpose

- Changes the owner of a file or directory.
- Usually requires `sudo` or root privileges.

## Syntax

```bash
sudo chown new_owner file_name
```

### Example

```bash
sudo chown mathu report.txt
```

This changes the owner of `report.txt` to `mathu`.

## Change Owner and Group Together

```bash
sudo chown owner:group file_name
```

Example:

```bash
sudo chown mathu:students report.txt
```

This changes:

- Owner to `mathu`
- Group to `students`

## Changing the Group with `chgrp`

## Purpose
- Changes only the group ownership of a file or directory.
## Syntax

```bash
sudo chgrp group_name file_name
```

### Example

```bash
sudo chgrp security access.log
```

This changes the group of `access.log` to `security`.


## `chmod`, `chown` and `chgrp` Summary

|Command|Purpose|Example|
|---|---|---|
|`chmod`|Change permissions|`chmod 750 file.txt`|
|`chown`|Change file owner|`sudo chown mathu file.txt`|
|`chown owner:group`|Change owner and group|`sudo chown mathu:students file.txt`|
|`chgrp`|Change group ownership|`sudo chgrp security file.txt`|

## Switching Between Users

## `su`

- `su` means **switch user**.
- It allows you to change to another user account.
- You normally need the other user’s password.


### Syntax

```bash
su username
```

### Example

```bash
su user2
```

After entering the password, the shell changes to `user2`.

## Login Shell

```bash
su -l user2
```

or:

```bash
su - user2
```

This:

- Switches to `user2`.
- Loads the new user’s environment.
- Moves to the new user’s home directory.

Example:

```bash
su - user2
pwd
```

Output:

```text
/home/user2
```

## `sudo` vs `su`

|Command|Meaning|
|---|---|
|`su user2`|Switch to another user|
|`su -`|Switch to the root user|
|`sudo command`|Run one command with elevated privileges|

Example:

```bash
sudo chmod 600 private.txt
```

> [!TIP]  
> Using `sudo` for one administrative command is usually safer than staying logged in as the root user.

## Why File Permissions Matter

- Protect sensitive files.
- Prevent unauthorized changes.
- Limit access to system configuration files.
- Control who can run scripts or programs.
- Reduce the damage caused by compromised accounts.
- Support the principle of least privilege.

## SOC Analyst Use Cases

|Task|Permission Knowledge Needed|
|---|---|
|Investigate suspicious scripts|Check whether the file is executable|
|Review sensitive logs|Confirm who can read the logs|
|Detect insecure files|Look for dangerous permissions such as `777`|
|Investigate file changes|Check owner and group information|
|Secure evidence|Restrict access using permissions such as `600`|
|Review web-server files|Confirm the service account has only required access|


## Security Example

A private key should not be accessible to other users.

```bash
chmod 600 private_key
```

Meaning:

```text
rw-------
```

- Owner can read and write.
- Group has no access.
- Others have no access.

## Important Commands

```bash
ls -l
chmod 755 script.sh
chmod 600 private.txt
chmod u+x script.sh
sudo chown mathu file.txt
sudo chown mathu:students file.txt
sudo chgrp security file.txt
su user2
su - user2
```

## Key Takeaways

- Linux permissions use `r`, `w` and `x`.
- Permissions are assigned to the owner, group and others.
- Numeric permissions use `4`, `2` and `1`.
- `chmod` changes permissions.
- `chown` changes ownership.
- `chgrp` changes group ownership.
- `ls -l` displays permissions, owner and group.
- Avoid giving more permissions than necessary.
- The principle of least privilege improves system security.
# 6. Users and Groups

## What Are Users and Groups?

- A **user** is an account that can access a Linux system.
- A **group** is a collection of users.
- Groups allow administrators to assign permissions to several users at once.
- Linux uses users and groups to control access to files, directories and system commands.
## User and Group Commands

| Command   | Purpose                                        | Syntax                  | Example                 | Example Output                                                | Why It Is Important                                              |
| --------- | ---------------------------------------------- | ----------------------- | ----------------------- | ------------------------------------------------------------- | ---------------------------------------------------------------- |
| `whoami`  | Shows the currently active user.               | `whoami`                | `whoami`                | `mathu`                                                       | Confirms which account is currently being used.                  |
| `id`      | Shows a user's UID, GID and group memberships. | `id [username]`         | `id mathu`              | `uid=1001(mathu) gid=1001(mathu) groups=1001(mathu),27(sudo)` | Helps identify the user's account and privileges.                |
| `sudo`    | Runs a command with administrator privileges.  | `sudo command`          | `sudo apt update`       | `[sudo] password for mathu:`                                  | Allows approved users to perform administrative tasks.           |
| `adduser` | Creates a new user account.                    | `sudo adduser username` | `sudo adduser analyst1` | `Adding user 'analyst1'...`                                   | Creates a separate account and home directory for a user.        |
| `passwd`  | Creates or changes a user's password.          | `passwd [username]`     | `sudo passwd analyst1`  | `passwd: password updated successfully`                       | Protects accounts and allows password resets.                    |
| `groups`  | Shows the groups a user belongs to.            | `groups [username]`     | `groups mathu`          | `mathu : mathu sudo security`                                 | Helps identify group-based permissions and administrator access. |

## Understanding the `id` Output

Example:

```bash
id mathu
```

Output:

```text
uid=1001(mathu) gid=1001(mathu) groups=1001(mathu),27(sudo),1002(security)
```

|Part|Meaning|
|---|---|
|`uid=1001(mathu)`|User ID and username|
|`gid=1001(mathu)`|Primary group ID and group name|
|`27(sudo)`|User belongs to the administrator group|
|`1002(security)`|User belongs to the security group|

## Important Terms

|Term|Meaning|
|---|---|
|UID|Unique number used to identify a user|
|GID|Unique number used to identify a group|
|Primary group|Main group assigned to a user|
|Secondary group|Additional group that a user belongs to|
|Root user|Administrator account with full system access|
|Normal user|Account with limited permissions|
|Service user|Account used by an application or service|

> [!NOTE]  
> The root user's UID is normally `0`.


## Users vs Groups

|Users|Groups|
|---|---|
|Represent individual accounts|Represent collections of users|
|Have a username and UID|Have a group name and GID|
|Can own files and directories|Can receive shared file permissions|
|Can belong to multiple groups|Can contain multiple users|

## `sudo` vs Root User

|Method|Meaning|
|---|---|
|`sudo command`|Run one command with administrator privileges|
|`su username`|Switch to another user|
|`su -`|Switch to the root account|
|`su - username`|Switch user and load that user's full environment|

Example:

```bash
sudo apt update
```

> [!WARNING]  
> Commands executed using `sudo` can modify or damage the system. Always check the command before running it.

## Simple Practical Example

Create a new user:

```bash
sudo adduser analyst1
```

Check the user's information:

```bash
id analyst1
```

Set or change the password:

```bash
sudo passwd analyst1
```

Check the user's groups:

```bash
groups analyst1
```

Confirm the current user:

```bash
whoami
```


## SOC Analyst Use Cases

|SOC Task|Relevant Command|
|---|---|
|Identify the active account|`whoami`|
|Check a user's UID and privileges|`id username`|
|Identify users with administrator access|`groups username`|
|Create a separate analyst account|`adduser`|
|Reset a compromised password|`passwd`|
|Run an approved administrative command|`sudo`|

## Common Security Risks

- Users sharing the same account.
- Weak or reused passwords.
- Unnecessary users in the `sudo` group.
- Old employee accounts remaining active.
- Service accounts having excessive permissions.
- Users receiving more access than required.

## Key Takeaways

- Users represent individual Linux accounts.
- Groups allow permissions to be shared among users.
- `whoami` shows the active user.
- `id` shows UID, GID and group memberships.
- `groups` displays a user's groups.
- `adduser` creates a new account.
- `passwd` changes a password.
- `sudo` runs commands with elevated privileges.
- Users should receive only the permissions required for their work.

# 7. Process Management

## What Is a Process?

A **process** is a program that is currently running
Examples:

- A web browser
- A terminal
- An SSH session
- A web server
- A background security service
Each process receives a unique number called a **Process ID**.

## Important Process Terms

|Term|Meaning|
|---|---|
|Process|A program that is currently running|
|PID|Process ID used to identify a running process|
|Parent process|The process that started another process|
|Foreground process|A process currently using the terminal|
|Background process|A process running without blocking the terminal|
|Job|A command started from the current shell|

## Process Management Commands

|Command|Purpose|Syntax|Example|Expected Output|Why It Is Important|
|---|---|---|---|---|---|
|`ps`|Shows running processes.|`ps [options]`|`ps aux`|A list containing users, PIDs, CPU usage, memory usage and commands|Helps identify running applications and suspicious processes.|
|`top`|Displays running processes in real time.|`top`|`top`|Live CPU, memory and process information|Useful for monitoring system performance.|
|`kill`|Sends a signal to a process using its PID.|`kill [signal] PID`|`kill 2451`|Usually no output when successful|Stops or controls one specific process.|
|`killall`|Stops processes using their process name.|`killall process_name`|`killall firefox`|Usually no output when successful|Stops all processes with the specified name.|
|`jobs`|Shows jobs started from the current shell.|`jobs`|`jobs`|`[1]+ Running python3 server.py &`|Helps manage commands running in the background.|

## Understanding `ps aux`

```bash
ps aux
```

Example output:

```text
USER       PID %CPU %MEM COMMAND
root         1  0.0  0.1 /sbin/init
mathu     2451  1.2  2.5 firefox
```

|Column|Meaning|
|---|---|
|`USER`|User running the process|
|`PID`|Process ID|
|`%CPU`|CPU usage|
|`%MEM`|Memory usage|
|`COMMAND`|Program or command being executed|

## Running a Background Process

Add `&` to the end of a command:

```bash
python3 server.py &
```

Example output:

```text
[1] 2451
```

|Value|Meaning|
|---|---|
|`1`|Job number|
|`2451`|Process ID|

Check the background job:

```bash
jobs
```

## Using `kill`

Stop a process normally:

```bash
kill 2451
```

Forcefully stop a process:

```bash
kill -9 2451
```

> [!WARNING]  
> Use `kill -9` only when a process does not stop normally. It immediately terminates the process without allowing it to close safely.

## SOC Use Cases

|Task|Command|
|---|---|
|Find suspicious processes|`ps aux`|
|Monitor CPU and memory usage|`top`|
|Stop a malicious process|`kill PID`|
|Stop all processes with one name|`killall name`|
|Review background commands|`jobs`|

# 8. Package Management

## What Is Package Management?

A **package** is a collection of files used to install software.

Ubuntu uses the **APT package manager** to:

- Install software
- Update package information
- Upgrade installed software
- Remove software
- Manage software dependencies
APT usually downloads packages from trusted software repositories.

## APT Commands

|Command|Purpose|Syntax|Example|Expected Output|Why It Is Important|
|---|---|---|---|---|---|
|`apt`|Manages software packages in Ubuntu.|`sudo apt [operation]`|`apt --help`|Displays available APT operations|Provides one main tool for package management.|
|`apt update`|Downloads the latest package information.|`sudo apt update`|`sudo apt update`|Repository information and available updates|Ensures the system knows about the latest packages.|
|`apt install`|Installs a package.|`sudo apt install package_name`|`sudo apt install nmap`|Package download and installation details|Adds required applications and tools.|
|`apt remove`|Removes an installed package.|`sudo apt remove package_name`|`sudo apt remove nmap`|Package removal details|Removes software that is no longer needed.|

## Important Difference

```bash
sudo apt update
```

This updates the **list of available packages**. It does not install the updates.

To install available upgrades:

```bash
sudo apt upgrade
```


## Typical Package Installation Process

```bash
sudo apt update
sudo apt install nmap
```

The first command refreshes the package list. The second installs Nmap.

> [!TIP]  
> Run `apt update` before installing software so that Ubuntu uses the latest package information.


# 9. Networking Commands

## Why Networking Commands Matter

Networking commands help you:

- View IP addresses
- Test connectivity
- Identify open ports
- View active connections
- Download files
- Investigate network problems
## Networking Commands

|Command|Purpose|Syntax|Example|Expected Output|
|---|---|---|---|---|
|`ip`|Displays and manages network interfaces, IP addresses and routes.|`ip [option]`|`ip addr`|Interfaces such as `lo` and `eth0`, with their IP addresses|
|`ifconfig`|Displays or configures network interfaces.|`ifconfig [interface]`|`ifconfig`|Interface names, IP addresses and packet information|
|`ping`|Tests connectivity to another host.|`ping [options] destination`|`ping -c 4 google.com`|Replies showing time and packet statistics|
|`hostname`|Displays or manages the system hostname.|`hostname [option]`|`hostname`|The computer's hostname|
|`ss`|Displays sockets, listening ports and network connections.|`ss [options]`|`ss -tuln`|TCP and UDP ports with local addresses|
|`netstat`|Displays network connections, routing and interface statistics.|`netstat [options]`|`netstat -tuln`|Active and listening network connections|
|`curl`|Transfers data to or from a URL.|`curl [options] URL`|`curl https://example.com`|Website source code or server response|
|`wget`|Downloads files from a URL.|`wget URL`|`wget https://example.com/file.txt`|Download progress and saved filename|

## `ip` Command Examples

Show IP addresses:

```bash
ip addr
```

Show routing information:

```bash
ip route
```

Show network interfaces:

```bash
ip link
```


## Understanding `ping`

```bash
ping -c 4 8.8.8.8
```

Example output:

```text
64 bytes from 8.8.8.8: icmp_seq=1 ttl=117 time=22.4 ms
```

|Part|Meaning|
|---|---|
|`64 bytes`|Size of the received response|
|`icmp_seq=1`|Sequence number|
|`ttl=117`|Time to live|
|`time=22.4 ms`|Response time|

> [!NOTE]  
> A failed ping does not always mean the target is offline. Some systems block ICMP traffic.

## Understanding `ss`

Show listening TCP and UDP ports:

```bash
ss -tuln
```

|Option|Meaning|
|---|---|
|`-t`|TCP connections|
|`-u`|UDP connections|
|`-l`|Listening sockets|
|`-n`|Show numerical addresses and ports|

Example output:

```text
Netid State  Local Address:Port
tcp   LISTEN 0.0.0.0:22
```

This means the system is listening for TCP connections on port `22`.

## `ss` vs `netstat`

|Command|Notes|
|---|---|
|`ss`|Modern and faster command|
|`netstat`|Older command that may not be installed by default|

Use `ss` when possible.

## `curl` vs `wget`

|Command|Best Used For|
|---|---|
|`curl`|Testing websites, APIs and HTTP responses|
|`wget`|Downloading files from the internet|

Examples:

```bash
curl -I https://example.com
```

Displays HTTP response headers.

```bash
wget https://example.com/report.pdf
```

Downloads the file.

## SOC Use Cases

|Task|Command|
|---|---|
|Check the system IP address|`ip addr`|
|Check network routes|`ip route`|
|Test connectivity|`ping`|
|Identify listening ports|`ss -tuln`|
|Check active connections|`ss -tunap`|
|Test a website response|`curl -I URL`|
|Download an investigation file|`wget URL`|

# 10. Searching and Filtering

## Searching Commands

|Command|Purpose|Syntax|Example|Expected Output|Why It Is Important|
|---|---|---|---|---|---|
|`find`|Searches for files and directories in real time.|`find location condition`|`find /home -name "*.txt"`|Paths of matching files|Finds files based on names, types, sizes or permissions.|
|`locate`|Searches for files using a prebuilt database.|`locate filename`|`locate passwd`|Paths containing the search term|Provides faster filename searches.|
|`grep`|Searches for text inside files or command output.|`grep [options] pattern file`|`grep "ERROR" system.log`|Lines containing `ERROR`|Useful for filtering logs and finding indicators.|
|`which`|Shows the executable used when a command runs.|`which command`|`which python3`|`/usr/bin/python3`|Confirms the command's executable path.|
|`whereis`|Finds executable, source and manual-page locations.|`whereis command`|`whereis python3`|Paths related to Python|Provides more locations than `which`.|


## Important `find` Examples

Search by exact filename:

```bash
find /home -name "passwords.txt"
```

Search for all text files:

```bash
find /home -name "*.txt"
```

Search only for directories:

```bash
find /home -type d -name "backup"
```

Search only for files:

```bash
find /var/log -type f
```

## Important `grep` Examples

Search for a word:

```bash
grep "failed" auth.log
```

Ignore uppercase and lowercase differences:

```bash
grep -i "error" system.log
```

Show line numbers:

```bash
grep -n "error" system.log
```

Search recursively:

```bash
grep -R "PRETTY_NAME" /etc/
```

Filter command output:

```bash
ps aux | grep ssh
```

## `find` vs `locate`

|Command|Difference|
|---|---|
|`find`|Searches the file system directly and gives current results|
|`locate`|Searches a database and is faster, but results may be outdated|

Update the `locate` database:

```bash
sudo updatedb
```


# 11. Compression and Archiving

## Compression vs Archiving

| Term               | Meaning                                     |
| ------------------ | ------------------------------------------- |
| Compression        | Reduces the size of a file                  |
| Archiving          | Combines several files into one file        |
| Compressed archive | Combines files and reduces their total size |

## Compression and Archiving Commands

|Command|Purpose|Syntax|Example|Expected Result|
|---|---|---|---|---|
|`zip`|Compresses files into a ZIP archive.|`zip archive.zip files`|`zip reports.zip report1.txt report2.txt`|Creates `reports.zip`|
|`unzip`|Extracts files from a ZIP archive.|`unzip archive.zip`|`unzip reports.zip`|Extracts files from the archive|
|`tar`|Creates or extracts archive files.|`tar [options] archive files`|`tar -cvf backup.tar Documents/`|Creates `backup.tar`|
|`gzip`|Compresses a single file using Gzip.|`gzip filename`|`gzip access.log`|Creates `access.log.gz`|
|`gunzip`|Decompresses a Gzip file.|`gunzip filename.gz`|`gunzip access.log.gz`|Restores `access.log`|

## Important `tar` Options

|Option|Meaning|
|---|---|
|`-c`|Create an archive|
|`-x`|Extract an archive|
|`-v`|Show files being processed|
|`-f`|Specify the archive filename|
|`-z`|Compress or decompress using Gzip|


## Common `tar` Examples

Create an archive:

```bash
tar -cvf backup.tar Documents/
```

Extract an archive:

```bash
tar -xvf backup.tar
```

Create a compressed archive:

```bash
tar -czvf backup.tar.gz Documents/
```

Extract a compressed archive:

```bash
tar -xzvf backup.tar.gz
```

> [!NOTE]  
> `tar` combines files into an archive. The `-z` option adds Gzip compression.

## Security Use Cases

- Archive investigation evidence.
- Compress large log files.
- Back up configuration files.
- Transfer several files as one archive.
- Preserve files before system changes.
# 12. System Monitoring

## System Monitoring Commands

|Command|Purpose|Syntax|Example|Expected Output|Why It Is Important|
|---|---|---|---|---|---|
|`df`|Shows file-system disk usage.|`df [options]`|`df -h`|Total, used and available disk space|Helps identify full disks and partitions.|
|`du`|Shows the space used by files or directories.|`du [options] path`|`du -sh /var/log`|Total size of `/var/log`|Helps locate directories consuming large amounts of storage.|
|`free`|Shows memory and swap usage.|`free [options]`|`free -h`|Total, used and available memory|Helps monitor RAM usage.|
|`uptime`|Shows how long the system has been running and its load averages.|`uptime`|`uptime`|Current time, uptime, users and load averages|Helps identify reboots and system load.|
|`history`|Displays previously executed shell commands.|`history`|`history`|Numbered list of commands|Useful for reviewing actions performed in the terminal.|

---

## `df` vs `du`

|Command|Shows|
|---|---|
|`df`|Disk usage of entire file systems or partitions|
|`du`|Disk usage of individual files and directories|

Examples:

```bash
df -h
```

```bash
du -sh /var/log
```

The `-h` option displays sizes in human-readable units such as MB and GB.

## Understanding `free -h`

```bash
free -h
```

Example output:

```text
              total        used        free      available
Mem:           15Gi        6Gi        2Gi          8Gi
Swap:           2Gi        0Gi        2Gi
```

|Field|Meaning|
|---|---|
|`total`|Total installed memory|
|`used`|Memory currently in use|
|`free`|Completely unused memory|
|`available`|Memory available for new applications|
|`Swap`|Disk space used when RAM is limited|

## Understanding `uptime`

```bash
uptime
```

Example output:

```text
13:10:22 up 5 days, 3:40, 2 users, load average: 0.20, 0.15, 0.10
```

|Part|Meaning|
|---|---|
|`13:10:22`|Current system time|
|`up 5 days`|Time since the last reboot|
|`2 users`|Number of logged-in users|
|`load average`|Average system workload|

## Important Note About `history`

```bash
history
```

This may reveal:

- Commands executed by the user
- Files accessed
- Administrative actions
- Investigation steps
- Mistakenly entered passwords or secrets

> [!WARNING]  
> Passwords, API keys and tokens should never be typed directly into commands because they may remain in shell history.

## SOC Use Cases

|Task|Command|
|---|---|
|Check available disk space|`df -h`|
|Find large log directories|`du -sh /var/log`|
|Check memory usage|`free -h`|
|Identify a recent reboot|`uptime`|
|Review previous commands|`history`|

# 13. Linux Log Files

## What Are Linux Logs?
Linux logs are records of events that happen on the system.
They may contain information about:
- User logins
- Authentication failures
- System errors
- Kernel events
- Service activity
- Network activity
- System startup
- Security incidents

Most traditional Linux log files are stored in:

```text
/var/log
```

## The `/var/log` Directory

The `/var/log` directory contains log files created by:

- The operating system
- Applications
- Background services
- Authentication systems
- The Linux kernel

View the directory:

```bash
ls -lh /var/log
```
## Common Linux Logs

|Log File|Information Contained|Security Importance|
|---|---|---|
|`/var/log/syslog`|General system messages, service activity, scheduled tasks and system errors|Useful for investigating system events and service failures|
|`/var/log/auth.log`|Login attempts, SSH activity, `sudo` usage and authentication failures|Very important for detecting unauthorized access|
|`/var/log/kern.log`|Messages generated by the Linux kernel, hardware and drivers|Useful for investigating kernel, driver and hardware problems|
|`/var/log/boot.log`|Messages produced during the system boot process|Helps identify startup failures and service-loading problems|

## `/var/log/syslog`

### Contains

- General operating-system messages
- Service start and stop events
- Scheduled task activity
- Application errors
- Network-related messages

Example:

```bash
less /var/log/syslog
```

Search for errors:

```bash
grep -i "error" /var/log/syslog
```

## `/var/log/auth.log`

### Contains

- Successful and failed logins
- SSH login attempts
- `sudo` command activity
- User authentication events
- Account and password-related activity

Example:

```bash
sudo less /var/log/auth.log
```

Search for failed logins:

```bash
sudo grep "Failed password" /var/log/auth.log
```

> [!IMPORTANT]  
> `auth.log` is one of the most useful Linux logs for SOC analysts because it records authentication and privilege-related events.

## `/var/log/kern.log`

### Contains

- Kernel messages
- Hardware events
- Driver problems
- Device errors
- Firewall-related kernel messages

Example:

```bash
sudo less /var/log/kern.log
```

Search for warnings:

```bash
sudo grep -i "warning" /var/log/kern.log
```
## `/var/log/boot.log`

### Contains

- System startup messages
- Services started during boot
- Services that failed to start
- Boot-related warnings and errors

Example:

```bash
sudo less /var/log/boot.log
```

## Useful Commands for Log Analysis

| Command   | Purpose                              | Example                  |
| --------- | ------------------------------------ | ------------------------ |
| `cat`     | Display a small log file             | `cat boot.log`           |
| `less`    | Read a large log file page by page   | `less syslog`            |
| `head`    | View the first lines                 | `head auth.log`          |
| `tail`    | View the latest lines                | `tail auth.log`          |
| `tail -f` | Monitor new log entries in real time | `tail -f auth.log`       |
| `grep`    | Search for specific events           | `grep "Failed" auth.log` |
| `wc -l`   | Count log entries                    | `wc -l access.log`       |

## Real-Time Log Monitoring

```bash
sudo tail -f /var/log/auth.log
```

This displays new authentication events as they are written to the log.

Press:

```text
Ctrl + C
```

to stop monitoring.

## Simple SOC Investigation Example

Search for failed SSH logins:

```bash
sudo grep "Failed password" /var/log/auth.log
```

Search for activity from a particular IP address:

```bash
sudo grep "192.168.1.50" /var/log/auth.log
```

Count the matching events:

```bash
sudo grep "Failed password" /var/log/auth.log | wc -l
```


## Important Notes

> [!NOTE]  
> Log names may differ between Linux distributions. For example, some distributions use `/var/log/secure` instead of `/var/log/auth.log`.

> [!NOTE]  
> Modern Linux systems may also store logs in the systemd journal, which can be viewed using the `journalctl` command.

# Quick Revision Summary

|Section|Important Commands|
|---|---|
|Process Management|`ps`, `top`, `kill`, `killall`, `jobs`|
|Package Management|`apt update`, `apt install`, `apt remove`|
|Networking|`ip`, `ping`, `hostname`, `ss`, `curl`, `wget`|
|Searching|`find`, `locate`, `grep`, `which`, `whereis`|
|Compression|`zip`, `unzip`, `tar`, `gzip`, `gunzip`|
|System Monitoring|`df`, `du`, `free`, `uptime`, `history`|
|Log Analysis|`less`, `tail -f`, `grep`, `wc -l`|

# Key Takeaways

- A process is a running program identified by a PID.
- APT manages software packages in Ubuntu.
- Networking commands help inspect addresses, ports and connections.
- `find` locates files, while `grep` searches inside files.
- Compression reduces file size, while archiving combines files.
- System-monitoring commands show disk, memory and system activity.
- Linux logs are mainly stored in `/var/log`.
- `auth.log` is especially important for investigating logins and privileged activity.
- `tail -f` and `grep` are essential commands for basic SOC log analysis.