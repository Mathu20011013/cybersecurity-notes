
# 1. Introduction to Windows

## What is Windows?

> **Microsoft Windows** is a graphical operating system (OS) developed by Microsoft that manages computer hardware, software, files, memory, and user interactions.

### Purpose

|Purpose|Explanation|
|---|---|
|Manage hardware|Controls CPU, memory, storage, keyboard, mouse, etc.|
|Run applications|Allows users to install and use software.|
|File management|Organizes files and folders.|
|User management|Supports multiple user accounts with different permissions.|
|Security|Protects the system using authentication, permissions, firewall, and antivirus.|
|Networking|Connects computers to local networks and the Internet.|


## Characteristics of Windows

|Feature|Explanation|
|---|---|
|**GUI (Graphical User Interface)**|Uses windows, icons, menus, and a mouse for easy interaction.|
|**Multi-user**|Supports multiple user accounts with separate settings and permissions.|
|**NT Kernel**|Core part of Windows that manages hardware, memory, and processes.|
|**Security**|Provides authentication, permissions, Defender, Firewall, BitLocker, and UAC.|
|**Networking**|Supports LAN, Wi-Fi, Internet, domains, file sharing, DNS, DHCP, and remote access.|

# 2. Windows Editions

|Edition|Purpose|
|---|---|
|**Home**|Designed for personal and home users. Includes basic Windows features.|
|**Pro**|Designed for professionals and small businesses. Includes BitLocker, Remote Desktop, Hyper-V, and Group Policy.|
|**Enterprise**|Designed for large organizations. Includes advanced security and centralized management features.|
|**Education**|Designed for schools and universities with educational features and licensing.|
|**Server**|Used to manage networks, users, databases, websites, file sharing, and enterprise services.|

### Quick Comparison

|Feature|Home|Pro|Enterprise|Education|Server|
|---|:-:|:-:|:-:|:-:|:-:|
|Personal use|✅|✅|❌|❌|❌|
|Business use|❌|✅|✅|❌|✅|
|Domain Join|❌|✅|✅|✅|✅|
|BitLocker|❌|✅|✅|✅|Depends|
|Active Directory Support|❌|Limited|✅|✅|✅|

# 3. Windows Architecture

Windows uses a layered architecture where applications interact with the operating system, and the operating system communicates with the hardware.

## Components of Windows Architecture

|Component|Explanation|
|---|---|
|**User Mode**|Runs user applications (e.g., Chrome, Word). It has limited access to hardware, improving system stability and security.|
|**Kernel Mode**|Core operating system mode with full access to hardware and system resources.|
|**Windows Kernel**|The heart of Windows. Manages memory, processes, CPU scheduling, and communication between software and hardware.|
|**HAL (Hardware Abstraction Layer)**|Acts as a bridge between Windows and hardware, allowing Windows to work with different hardware without major changes.|
|**Device Drivers**|Software that enables Windows to communicate with hardware devices such as printers, keyboards, GPUs, and network cards.|
|**Services**|Background programs that perform system tasks without user interaction (e.g., Windows Update, Print Spooler, DHCP Client).|


## Cybersecurity Perspective 

|Component|Why is it important for Security Analysts?|
|---|---|
|User Mode|Malware often starts by running in user mode.|
|Kernel Mode|Kernel-level malware (rootkits) can gain full control of the system.|
|Windows Kernel|A common target for privilege escalation attacks.|
|HAL|Helps Windows communicate safely with hardware.|
|Device Drivers|Vulnerable or malicious drivers can be exploited by attackers.|
|Services|Attackers may create or modify services to maintain persistence.|

**Note:** This cybersecurity perspective is worth including because it connects your Windows knowledge to SOC and Security Analyst responsibilities, making your notes more useful for interviews and future projects.


# 4. Windows Boot Process

## Windows Boot Process

|Step|Explanation|
|---|---|
|**BIOS (Basic Input/Output System)**|Legacy firmware that initializes hardware and starts the boot process.|
|**UEFI (Unified Extensible Firmware Interface)**|Modern replacement for BIOS. Supports Secure Boot, faster startup, and large hard drives.|
|**Windows Boot Manager (bootmgr)**|Finds the Windows installation and starts the Windows loader.|
|**Winload.exe**|Loads the Windows kernel, drivers, and essential system files into memory.|
|**Kernel Loading**|The Windows kernel initializes hardware, memory, drivers, and system services.|
|**Logon Screen**|Windows displays the sign-in screen where users enter their credentials.|

### Windows Boot Process Flow

```text
Power ON
     │
     ▼
 BIOS / UEFI
     │
     ▼
Windows Boot Manager
     │
     ▼
 Winload.exe
     │
     ▼
 Windows Kernel
     │
     ▼
 Logon Screen
```

### Cybersecurity Note

| Component    | Security Importance                                           |
| ------------ | ------------------------------------------------------------- |
| UEFI         | Supports **Secure Boot** to prevent unauthorized bootloaders. |
| Boot Manager | Ensures the correct operating system starts.                  |
| Winload.exe  | Loads trusted system files required by Windows.               |

# 5. Windows User Interface

|Component|Purpose|
|---|---|
|**Desktop**|Main workspace where icons, files, and shortcuts are displayed.|
|**Start Menu**|Opens installed applications, settings, and power options.|
|**Taskbar**|Displays running applications and pinned programs.|
|**Notification Area (System Tray)**|Shows system status, clock, network, volume, battery, and notifications.|
|**File Explorer**|Used to browse and manage files, folders, and drives.|
|**Search**|Quickly finds applications, files, folders, and settings.|
|**Settings**|Modern interface for configuring Windows features and preferences.|
|**Control Panel**|Traditional tool for advanced system configuration and administration.|

> **Note:** Most daily Windows tasks are performed using these interface components.


# 6. File System

## What is a File System?

A **file system** is the method used by an operating system to **store, organize, and manage files and folders** on a storage device.
## Comparison of Windows File Systems

| Feature                |           FAT32           |             exFAT              |         NTFS          |
| ---------------------- | :-----------------------: | :----------------------------: | :-------------------: |
| Maximum file size      |         **4 GB**          |           Very large           |      Very large       |
| Maximum partition size |        Up to 2 TB         |           Very large           |      Very large       |
| Security permissions   |           ❌ No            |              ❌ No              |         ✅ Yes         |
| File compression       |             ❌             |               ❌                |           ✅           |
| File encryption        |             ❌             |               ❌                |           ✅           |
| Journaling             |             ❌             |               ❌                |           ✅           |
| Best use               | USB drives, older devices | Flash drives, external storage | Windows system drives |

## NTFS Features

|Feature|Description|
|---|---|
|**Permissions**|Controls which users can read, write, or modify files and folders.|
|**Compression**|Reduces file size to save disk space.|
|**Encryption (EFS)**|Encrypts files to protect sensitive data from unauthorized access.|
|**Journaling**|Records file system changes to help recover data after crashes or power failures.|
|**Quotas**|Limits the amount of disk space each user can use.|

## Why NTFS is Preferred in Windows

|Reason|Benefit|
|---|---|
|Better security|Supports file and folder permissions.|
|Reliable|Uses journaling to reduce data loss.|
|Large file support|Can store files larger than 4 GB.|
|Data protection|Supports encryption and compression.|
|Enterprise ready|Suitable for business and organizational use.|

## Cybersecurity Perspective 

|Feature|Why is it Important for Security Analysts?|
|---|---|
|NTFS Permissions|Prevents unauthorized access to sensitive files.|
|Encryption (EFS)|Protects confidential data if a device is compromised.|
|Journaling|Helps recover data and investigate system issues.|
|Quotas|Prevents users from consuming excessive disk space.|
# 7. Important Windows Directories

## Windows Directory

### What is the Windows Directory?

- Default location: **`C:\Windows`**
- Contains the Windows operating system files.
- Can be installed on another drive (not necessarily C:).
- The system environment variable for the Windows folder is **`%windir%`**.

> **Environment Variable:** A variable that stores system information, such as Windows location, temporary folders, and system paths.

## Important Windows Directories

| Directory               | Purpose                                                                     |
| ----------------------- | --------------------------------------------------------------------------- |
| **C:\Windows**          | Main folder containing Windows operating system files.                      |
| **System32**            | Stores essential system files, DLLs, drivers, and Windows utilities.        |
| **SysWOW64**            | Contains 32-bit system files used by 32-bit applications on 64-bit Windows. |
| **Users**               | Stores user profiles (Desktop, Documents, Downloads, etc.).                 |
| **Program Files**       | Default location for 64-bit installed applications.                         |
| **Program Files (x86)** | Default location for 32-bit applications on 64-bit Windows.                 |
| **Temp**                | Stores temporary files created by Windows and applications.                 |
| **AppData**             | Stores user-specific application settings, cache, and configuration files.  |

## User Profile Folder

Every user has a personal profile stored in:

```
C:\Users\<Username>
```

Example:

```
C:\Users\Mathu
```

Common folders inside a user profile:

- Desktop
- Documents
- Downloads
- Pictures
- Music
- Videos

## Important Note

> **Do not delete files from `C:\Windows` or `System32`.** These folders contain critical operating system files, and deleting them may prevent Windows from working properly.

## Cybersecurity Perspective 

|Directory|Why is it Important?|
|---|---|
|**System32**|Malware may replace or abuse system files.|
|**Users**|User documents and downloads are common malware targets.|
|**Temp**|Malware often stores temporary files here.|
|**AppData**|Many applications—and some malware—store files here for persistence.|

# 8. User Accounts and Groups

## What is a User Account?

A **user account** allows a person to log in and use the Windows operating system.
The account type determines **what actions the user can perform** on the computer.
## Types of User Accounts

| Account Type          | Description                                                                                                                |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| **Administrator**     | Has full control over the system. Can install software, change settings, create or delete users, and manage groups.        |
| **Standard User**     | Can use installed programs and manage personal files but cannot make system-wide changes without administrator permission. |
| **Guest**             | Temporary account with very limited permissions (disabled by default in modern Windows).                                   |
| **Local User**        | Account stored only on the local computer.                                                                                 |
| **Microsoft Account** | Online account used to sign in to Windows and synchronize settings across devices.                                         |

## Administrator vs Standard User

|Feature|Administrator|Standard User|
|---|---|---|
|Install software|✅|❌ (Requires admin approval)|
|Change system settings|✅|❌|
|Create or delete users|✅|❌|
|Modify personal files|✅|✅|
|Manage groups|✅|❌|

## User Profile

When a new user logs in for the first time:

- Windows automatically creates a **user profile**.
- The profile is stored in:

```
C:\Users\<Username>
```

# Windows Groups

## What is a Group?

A **group** is a collection of users with the same permissions.
Instead of assigning permissions to each user individually, administrators assign users to groups.
> A user can belong to **multiple groups** and inherits the permissions of each group.

## Important Windows Groups

|Group|Purpose|
|---|---|
|**Administrators**|Full control over the computer.|
|**Users**|Standard users with limited permissions.|
|**Guests**|Temporary users with restricted access.|
|**Backup Operators**|Can back up and restore files regardless of file permissions.|
|**Remote Desktop Users**|Allowed to connect to the computer using Remote Desktop.|

## Local Users and Groups

Windows provides **Local Users and Groups Management** to manage local accounts and groups.
Run:

```
lusrmgr.msc
```

From here, you can:
- View local users
- View local groups
- Create users
- Delete users
- Add users to groups
- Modify group membership
# User Account Control (UAC)

## What is UAC?
**User Account Control (UAC)** is a Windows security feature that prevents unauthorized system changes.
When an administrator performs an action requiring elevated privileges (such as installing software), Windows displays a confirmation prompt before allowing the action.

## Why is UAC Important?

|Benefit|Explanation|
|---|---|
|Prevents unauthorized changes|Stops programs from making system changes without approval.|
|Protects against malware|Malware cannot easily gain administrator privileges.|
|Improves system security|Requires user confirmation before sensitive actions.|

## Cybersecurity Perspective 

| Topic                  | Why is it Important for Security Analysts?                            |
| ---------------------- | --------------------------------------------------------------------- |
| Administrator Accounts | Attackers often try to obtain administrator privileges.               |
| Standard Users         | Using standard accounts reduces the impact of malware.                |
| User Groups            | Incorrect group membership can lead to privilege escalation.          |
| UAC                    | Helps prevent unauthorized software installation and privilege abuse. |
| AppData & Temp         | Common locations where malware stores files.                          |

## Quick Revision

| Item          | Remember                                        |
| ------------- | ----------------------------------------------- |
| `%windir%`    | Windows directory environment variable          |
| `C:\Windows`  | Windows operating system files                  |
| `System32`    | Critical Windows system files                   |
| `C:\Users`    | User profile location                           |
| `lusrmgr.msc` | Local Users and Groups Management               |
| Administrator | Full system control                             |
| Standard User | Limited permissions                             |
| UAC           | Requests permission before system-level changes |

# 9. NTFS Permissions

## What are NTFS Permissions?

NTFS permissions control **who can access a file or folder** and **what actions they are allowed to perform**.
They help protect files from unauthorized access and modification.

## Common NTFS Permissions

|Permission|Meaning|
|---|---|
|**Read**|View or open files and folders without making changes.|
|**Write**|Create new files/folders and modify existing file content.|
|**Modify**|Read, write, delete, and edit files or folders.|
|**Execute**|Run executable files or programs.|
|**Full Control**|Complete access, including reading, writing, deleting, changing permissions, and taking ownership.|

## Permission Hierarchy

```text
Read
   ↓
Write
   ↓
Modify
   ↓
Full Control
```

## Why are NTFS Permissions Important?

|Benefit|Explanation|
|---|---|
|Protect data|Prevent unauthorized users from accessing files.|
|Control user access|Different users can have different permission levels.|
|Improve security|Reduces accidental or malicious file modifications.|
|Support organizations|Allows administrators to manage file access efficiently.|

## Cybersecurity Perspective 

|Permission|Why is it Important for Security Analysts?|
|---|---|
|Read|Sensitive files should only be readable by authorized users.|
|Write|Excessive write permissions may allow malware to modify files.|
|Modify|Attackers may abuse this permission to alter or delete important data.|
|Execute|Malware often requires execute permission to run.|
|Full Control|Should only be granted to trusted administrators.|

# 10. Windows Services

## What is a Windows Service?

A **Windows Service** is a program that runs **in the background** without user interaction.
Services usually start automatically when Windows boots and perform important system tasks.

## Characteristics of Windows Services

- Run in the background.
- Start automatically or manually.
- Support Windows and application functions.
- Continue running even if no user is logged in.
## Common Windows Services

|Service|Purpose|
|---|---|
|**Windows Update**|Downloads and installs Windows updates and security patches.|
|**Print Spooler**|Manages print jobs sent to printers.|
|**Microsoft Defender**|Provides real-time antivirus and malware protection.|
|**DHCP Client**|Automatically obtains an IP address and network settings from a DHCP server.|

## Service Startup Types

| Startup Type  | Description                                       |
| ------------- | ------------------------------------------------- |
| **Automatic** | Starts automatically when Windows starts.         |
| **Manual**    | Starts only when needed or when a user starts it. |
| **Disabled**  | Cannot start until it is enabled.                 |

## Managing Windows Services

To open the Services console:

```text
services.msc
```

From here, you can:

- Start a service
- Stop a service
- Restart a service
- Change the startup type
- View service properties

## Quick Revision

|Item|Remember|
|---|---|
|**NTFS Permissions**|Control access to files and folders.|
|**Read**|View only.|
|**Write**|Create or edit files.|
|**Modify**|Read, write, and delete.|
|**Execute**|Run programs.|
|**Full Control**|Complete access.|
|**Windows Service**|Background program that performs system tasks.|
|**services.msc**|Opens the Windows Services management console.|
# **Windows Fundamentals 2 — Short Notes**

## **1. System Configuration — `msconfig`**

Used to **troubleshoot Windows startup problems**. Requires administrator permissions.

Open: **Win + R → `msconfig`**

|Tab|Purpose|
|---|---|
|**General**|Choose what Windows loads during startup.|
|**Boot**|Configure boot options, such as Safe boot.|
|**Services**|View services and enable/disable them for troubleshooting.|
|**Startup**|Directs you to Task Manager to manage startup apps on Windows client systems.|
|**Tools**|Launch other Windows administration tools.|

**General tab startup modes:**

- **Normal:** Loads the usual drivers and services.
- **Diagnostic:** Loads only basic devices and services to help identify problems.
- **Selective:** Lets you choose which startup items and services load.

**Startup applications:**

- Applications configured to start automatically when a user signs in.
- On Windows 10/11, manage them through **Task Manager → Startup / Startup apps**.
- In the lesson’s Windows Server VM, check **Win + R → `shell:startup`**.
- This opens the current user’s Startup folder. It shows items in that folder, **not every possible automatic startup item**.

**Tools tab:** Select a tool → view its **Selected command** → click **Launch**.

## **2. Advanced System Settings**

Search **View advanced system settings** to open System Properties.

**Page file / virtual memory**

- A **page file** uses disk space to support memory management.
- Windows can move some memory contents from RAM to the page file.
- It helps support applications when memory demand is high, but **disk is slower than RAM**.

**Path:** Advanced → Performance **Settings** → Advanced → Virtual memory **Change**.

Shows the drive, initial size, maximum size and whether Windows manages the size automatically.

**Startup and Recovery**

- Windows can save a **crash dump** after a serious system crash, such as a Blue Screen of Death.
- A crash dump contains information used to investigate the cause.

**Path:** Advanced → Startup and Recovery **Settings** → Write debugging information.

|Dump type|Simple meaning|
|---|---|
|**Small memory dump**|Basic crash information; smallest file.|
|**Kernel memory dump**|Memory information related to the Windows kernel.|
|**Complete memory dump**|Captures physical memory contents; largest option.|
|**Automatic memory dump**|Similar to a kernel dump, with automatic page-file management.|
|**None**|No crash dump saved.|

## **3. User Account Control — UAC**

UAC asks for permission when an action needs **administrator privileges**, such as installing software or changing protected settings.

- An administrator normally receives a **Yes/No** prompt.
- A standard user normally needs **administrator credentials**.

|Level|Behaviour|
|---|---|
|**Always notify**|Prompts for apps and your own Windows setting changes that require elevation; dims the desktop.|
|**Notify for apps — default**|Prompts when apps try to make changes; usually does not prompt for your own Windows setting changes; dims the desktop.|
|**Notify without dimming**|Same notification behaviour as above, but without the protected, dimmed desktop.|
|**Never notify**|Suppresses UAC prompts for administrators; reduces protection.|

**Dimming the desktop** indicates the prompt is on the **Secure Desktop**, helping protect it from interference by other applications.

## **4. Computer Management — `compmgmt.msc`**

Combines administration tools into three sections:

- **System Tools**
- **Storage**
- **Services and Applications**

**System Tools**

|Tool|Purpose / example|
|---|---|
|**Task Scheduler**|Automatically runs programs or scripts at a specified time or trigger. Example: daily backup at 10 AM.|
|**Event Viewer**|Shows recorded events to troubleshoot problems and investigate activity.|
|**Shared Folders**|Shows network shares, connected users and remotely opened files.|
|**Local Users and Groups**|Manages local accounts and group membership.|
|**Performance Monitor**|Tracks performance counters, such as CPU usage, live or from logs.|
|**Device Manager**|Views hardware and manages devices and drivers.|

**Task Scheduler**

- **Trigger:** When the task runs, such as at sign-in or every day.
- **Action:** What it runs, such as a program or script.
- Tasks can run **once** or **repeatedly**.
- **Task Scheduler Library:** Browse tasks; check subfolders too.
- **Create Basic Task:** Create a simple scheduled task.

**Event Viewer**

Three panes: **Left = select logs; Middle = view events; Right = actions.**

The lesson uses these five traditional event categories: [Microsoft Learn](https://learn.microsoft.com/en-us/windows/win32/eventlog/event-types?utm_source=chatgpt.com)

|Event category|Meaning|
|---|---|
|**Error**|A significant problem, such as a service failing to start.|
|**Warning**|A possible problem, such as low disk space.|
|**Information**|General information about normal operation.|
|**Success Audit**|An audited security action succeeded, such as a successful login.|
|**Failure Audit**|An audited security action failed, such as a failed login.|

Main logs: **Application** records application events, **Security** records audited security activity, and **System** records Windows component events. Applications can also create custom logs. [Microsoft Learn](https://learn.microsoft.com/en-us/windows/win32/eventlog/eventlog-key?utm_source=chatgpt.com)

**Shared Folders**

- **Shares:** Folders available over the network.
- **Sessions:** Users currently connected to shares.
- **Open Files:** Files currently opened through those connections.
- **`C$`:** Administrative share for the C: drive.
- **`ADMIN$`:** Administrative share for the Windows directory.
- **Permissions:** Determine who can access a share and what they can do.

**Storage → Disk Management**

Used to:

- Set up new disks and create volumes.
- Extend or shrink volumes.
- Assign or change drive letters, such as `E:`.

**Services and Applications**

A **service** is a program that runs in the background, such as Windows Update.

Service properties show its **display name, service name, executable path and startup type**.

|Startup type|Meaning|
|---|---|
|**Automatic**|Starts automatically during system startup.|
|**Manual**|Starts when requested by a user, application or system trigger.|
|**Disabled**|Cannot start until its startup type is changed.|

**Status** tells you whether a service is running now. **Startup type** tells you how it is configured to start.

**WMI — Windows Management Instrumentation**

- Allows tools and scripts to query and manage Windows locally or remotely.
- Example: PowerShell queries information about installed hardware.
- **WMIC** is the older, deprecated command-line tool; **WMI itself is not deprecated**.

## **5. System Information — `msinfo32.exe`**

Displays detailed information about the computer’s **hardware and software**.

|Section|Information shown|
|---|---|
|**System Summary**|OS version, system name, processor, BIOS and RAM.|
|**Hardware Resources**|Low-level hardware resource assignments, such as IRQs and memory addresses.|
|**Components**|Device details, such as display, input and network adapters.|
|**Software Environment**|Drivers, services, environment variables and other software details.|

Use the search bar to find details such as **IP address**.

**Environment variables**

Named values that tell Windows and programs where important resources are located.

|Variable|Purpose / typical value|
|---|---|
|**`WINDIR`**|Windows installation folder, usually `C:\Windows`.|
|**`TEMP`**|Folder used to store temporary files.|
|**`PATH`**|Folders searched when you run a command without its full path.|
|**`ComSpec`**|Command interpreter path, usually `C:\Windows\System32\cmd.exe`.|

**Example:** A program reads `TEMP` to know where to save temporary files without hard-coding a folder location.

View/edit: **Advanced system settings → Environment Variables**.

**Lab answers:**

- System Information executable: **`msinfo32.exe`**
- System Name: Read it from **System Summary** in your VM.
- ComSpec: Check the VM’s actual value under **Software Environment → Environment Variables**.

## **6. Resource Monitor — `resmon`**

Shows how running processes use resources.

|Resource|What to check|
|---|---|
|**CPU**|Which processes use processing power.|
|**Memory**|Which processes use RAM.|
|**Disk**|Which processes read/write data.|
|**Network**|Which processes send/receive data.|

Useful for investigating slow computers, unresponsive applications and file-locking problems.

**Example:** If the computer is slow, check which process is using a large amount of CPU or disk activity.

## **7. Windows Registry — `regedit`**

A central, hierarchical database that stores Windows configuration, including:

- User profiles and preferences.
- Application settings.
- Hardware and driver settings.
- File associations, such as which app opens a file type.

**Keys** are like folders; **values** hold the settings.

Open Registry Editor: **Win + R → `regedit`**.

**Be careful:** Incorrect registry changes can break applications or Windows. Back up relevant keys before editing.

**Commands to remember**

|Command|Opens|
|---|---|
|`msconfig`|System Configuration|
|`taskmgr`|Task Manager|
|`compmgmt.msc`|Computer Management|
|`lusrmgr.msc`|Local Users and Groups|
|`perfmon`|Performance Monitor|
|`msinfo32.exe`|System Information|
|`resmon`|Resource Monitor|
|`regedit`|Registry Editor|
|`shell:startup`|Current user’s Startup folder, through Run|