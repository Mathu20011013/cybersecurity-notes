
# Active Directory and Windows Domain

## 1. Why do companies use them?

Managing accounts and settings separately on **5 computers** is
manageable. Doing the same on **157 computers across four offices**
takes too much work.

A Windows domain lets IT **manage users and computers centrally**.

## 2. Main terms

  -----------------------------------------------------------------------
  Term                                Simple meaning
  ----------------------------------- -----------------------------------
  **Windows domain**                  A group of users and computers
                                      managed centrally by an
                                      organisation

  **Active Directory (AD)**           A directory service that stores and
                                      organises information about users,
                                      computers and groups

  **Domain Controller (DC)**          A server running Active Directory
                                      Domain Services and handling domain
                                      authentication

  **Group Policy**                    A way to apply settings centrally
                                      to users and computers

  **Authentication**                  Checking who you are

  **Authorisation**                   Checking what you are allowed to
                                      access
  -----------------------------------------------------------------------

> A Windows domain is different from a website domain such as
> `example.com`, although Windows domains also use DNS names.

## 3. ABC Company example

ABC Company has **100 computers and 200 employees**.

IT first:

1.  Sets up a Domain Controller.
2.  Connects the computers and server through a network.
3.  Installs Windows and required applications on the computers.
4.  **Joins each computer to the domain.**

**Joining a domain** means enrolling a computer into the company's
centrally managed environment. Connecting to company Wi-Fi alone does
not join it.

### A new employee joins

IT creates one domain account for Mathu:

    ABC\Mathu

-   `ABC` = domain name.
-   `Mathu` = username.

IT does **not** need to create a separate local account for Mathu on
every PC.

### Mathu signs in to PC-01

1.  Mathu enters his domain username and password.
2.  PC-01 contacts a Domain Controller.
3.  The DC verifies the credentials.
4.  Windows allows sign-in if the account is authorised.
5.  On the first sign-in, PC-01 normally creates a local profile for
    Mathu.

Mathu can later sign in to **PC-02 using the same domain account**, if
permitted.

## 4. Local account versus domain account

  -----------------------------------------------------------------------
  Local account                       Domain account
  ----------------------------------- -----------------------------------
  Managed on one computer             Managed centrally in Active
                                      Directory

  Example: `MATHU-13\Mathu13`         Example: `ABC\Mathu`

  Creating the same username on       The same domain identity can be
  another PC creates a separate       used on permitted domain computers
  account                             
  -----------------------------------------------------------------------

Local accounts can still exist on a domain-joined computer.

## 5. Account versus profile

-   **Account:** Your identity and associated permissions.
-   **Profile:** Your personal settings and folders on a computer.

The same domain account can have a **separate local profile on each
PC**.

> The same username and password do not automatically bring your files
> to another computer.

## 6. Where is your work stored?

**Active Directory manages identities; it does not automatically store
your documents.**

  -----------------------------------------------------------------------
  Save location           Where the file is       Accessible from another
                          stored                  PC?
  ----------------------- ----------------------- -----------------------
  Local Documents/Desktop On that PC              Not automatically
  without syncing                                 

  Company shared folder   On a file server        Yes, with network
                                                  access and permission

  Company OneDrive        Cloud storage, with     Yes, after syncing and
                          local copies depending  signing in
                          on settings             
  -----------------------------------------------------------------------

### Example

Mathu creates `Report.docx` on PC-01.

-   Saved locally → it stays on **PC-01**.
-   Saved to `\\FileServer\Finance` → Mathu can open it from **PC-02**,
    if authorised.
-   Saved to a synced OneDrive folder → it becomes available through
    OneDrive after syncing.

Some companies automatically redirect or sync Documents/Desktop.

## 7. How groups control access

IT creates groups such as:

  Group        Example permission
  ------------ ----------------------------------
  Finance      Access finance shared folders
  HR           Access employee records
  IT Support   Perform authorised support tasks

IT adds Mathu to **Finance**, then grants that group access to the
finance folder.

**AD stores group membership. The resource, such as the file server,
checks permissions.**

Being a domain user does not mean having administrator rights or access
to everything.

## 8. How settings are managed centrally

Using **Group Policy**, IT can configure:

-   Password requirements.
-   Automatic screen locking.
-   Firewall settings.

Relevant computers retrieve and apply these settings.

**An offline computer cannot receive new policies until it reconnects.**
Some changes require sign-out or restart.

## 9. Does it need the internet?

**It needs network connectivity to the Domain Controller---not
necessarily the public internet.**

  -----------------------------------------------------------------------
  Connection                          Meaning
  ----------------------------------- -----------------------------------
  **LAN --- Local Area Network**      Connects devices within an office
                                      through cables or Wi-Fi

  **Internet**                        Connects networks worldwide

  **VPN --- Virtual Private Network** Provides a protected connection to
                                      another network
  -----------------------------------------------------------------------

If the office internet fails but the office LAN and DC still work,
domain communication can continue.

Without access to a DC:

-   First-time domain sign-in on that PC normally cannot complete.
-   A previous user may sign in using **cached logon information**, if
    enabled.
-   New policies cannot be retrieved.
-   Resources requiring domain validation may be unavailable.

**Cached logon information:** Information retained locally to verify a
previous user's sign-in when a DC is unavailable.

## 10. Where does the Domain Controller run?

It can run on:

-   A physical server in the office.
-   A virtual machine on company hardware.
-   A cloud virtual machine, such as an Azure VM.

**The company does not always need to buy a separate physical server.**
A cloud server still runs on physical hardware owned by the cloud
provider.

## 11. Working from home

Example: Mathu works from Batticaloa while ABC's server is in Colombo.

1.  Connect to home internet.
2.  Connect the **company VPN**.
3.  The VPN provides access to the company network.
4.  The laptop can reach permitted company resources and the DC.

A laptop may use cached sign-in first, then connect the VPN. A
first-time domain sign-in needs appropriate DC connectivity, such as a
company-configured pre-sign-in VPN.

> A consumer VPN does not automatically connect you to your company
> network.

## 12. What is RDP?

**RDP = Remote Desktop Protocol.**

It lets you view and control another computer's desktop over a network.

### Example

Mathu uses his home laptop to connect to his office PC through RDP.

  Activity                                         Where it happens
  ------------------------------------------------ ----------------------
  Physical typing and mouse movement               Home laptop
  Word runs                                        Office PC
  Saving to the remote session's local Documents   Office PC
  Viewing the remote desktop                       Home laptop's screen

The remote computer must be powered on, reachable and configured to
allow the connection.

-   **VPN:** Connects you to a network.
-   **RDP:** Lets you control a computer's desktop.
-   **AD:** Manages domain identities, computers and groups.
-   **File server:** Stores shared files.

## Key idea to remember

> ABC Company sets up each PC and joins it to the domain. IT creates
> employee accounts centrally in AD. Employees sign in to permitted
> computers using their domain accounts. Their files are available
> across PCs only when shared storage or syncing is configured.

# **Active Directory (AD DS) -- Simple Notes**

## **1. Active Directory (AD DS)**

Active Directory Domain Services (AD DS) is a central directory that
stores and manages information about objects in a Windows network.

It manages:

-   Users
-   Computers
-   Groups
-   Printers
-   Shared resources

Example: In a company, Active Directory helps IT administrators manage
all employees' accounts and computers from one central place.

## **2. Users**

Users are accounts that can be authenticated and given permissions to
access network resources.

There are two common types:

-   **People:** Employee accounts used to log in.
-   **Services:** Accounts used by applications or services to run, such
    as database services.

Example: An HR employee has a user account to log in and access HR
files.

## **3. Machines (Computers)**

When a computer joins an Active Directory domain, a machine account is
created.

-   Each domain-joined computer has its own account.
-   Machine accounts are security principals.
-   Machine account names usually end with `$`.
-   Machine account passwords are automatically changed periodically.

Example: A computer named `PC01` has an AD machine account called
`PC01$`.

## **4. Security Groups**

Security groups allow administrators to assign permissions to multiple
users or computers at once.

Instead of giving permission to each user individually, the
administrator adds users to a group.

  -----------------------------------------------------------------------
  Group                               Purpose
  ----------------------------------- -----------------------------------
  Domain Admins                       Administrate the entire domain

  Server Operators                    Manage certain Domain Controller
                                      operations

  Backup Operators                    Perform backup-related operations
                                      with special privileges

  Account Operators                   Manage certain domain accounts

  Domain Users                        Contains domain user accounts

  Domain Computers                    Contains domain computer accounts

  Domain Controllers                  Contains Domain Controller computer
                                      accounts
  -----------------------------------------------------------------------

Example: Instead of giving 10 employees access to a shared folder one by
one, the administrator can give permission to a group and add those
employees to it.

## **5. Active Directory Users and Computers**

**Active Directory Users and Computers (ADUC)** is a Windows
administrative tool used to manage Active Directory objects.

Administrators can use it to:

-   Create users and computers.
-   Create and manage groups.
-   Reset passwords.
-   Move objects between OUs.
-   Manage account settings. \## **6. Organizational Units (OUs)**

An **OU (Organizational Unit)** is a container used to organize users
and computers within Active Directory.

OUs are often organized according to departments.

Example:

-   IT OU → IT employees and computers.
-   HR OU → HR employees and computers.
-   Finance OU → Finance employees and computers.

Administrators can apply different Group Policies to different OUs.

## **7. Default Active Directory Containers**

  Container                  Purpose
  -------------------------- ---------------------------------------------------
  Builtin                    Contains built-in groups
  Computers                  Default location for computers joining the domain
  Domain Controllers         Contains Domain Controllers
  Users                      Contains default users and groups
  Managed Service Accounts   Contains managed service accounts

## **8. Security Groups vs OUs**

**OUs = Organize and apply policies**

**Security Groups = Grant permissions**

  -----------------------------------------------------------------------
  OU                                  Security Group
  ----------------------------------- -----------------------------------
  Organizes users and computers       Groups users and computers for
                                      permission management

  Used to apply policies (GPOs)       Used to grant access to resources

  A user belongs directly to one OU   A user can belong to multiple
  at a time                           security groups
  -----------------------------------------------------------------------

Simple example:

A company has 10 HR employees.

-   The **HR OU** organizes their accounts and allows HR-specific
    policies to be applied.
-   The **HR Security Group** can be given permission to access the HR
    shared folder.

**Remember these 5 concepts:**

-   **AD DS** -- Central management of a Windows domain.
-   **Users** -- Accounts representing people or services.
-   **Machines** -- Computers joined to the domain.
-   **Groups** -- Used to grant permissions.
-   **OUs** -- Used to organize objects and apply policies.

## **Active Directory -- OU Management & Delegation**

### **1. Deleting OUs**

-   OUs are protected against accidental deletion by default.
-   To remove this protection, enable **Advanced Features** in the AD
    Users and Computers (ADUC) View menu.
-   Go to the OU **Properties → Object** tab.
-   Uncheck **Protect object from accidental deletion**.
-   Then delete the OU.

Deleting an OU may also delete the users, groups and child OUs inside
it.

### **2. Delegation of Control**

**Delegation** allows an administrator to give a specific user
permission to perform certain administrative tasks on an OU without
giving them full Domain Administrator privileges.

-   Delegation can be assigned to specific users.
-   Permissions can be limited to particular OUs.
-   It reduces the need for Domain Administrators to perform routine
    tasks.

Example concept: IT Support may be allowed to reset passwords for users
in certain departments without having full domain administration
privileges.

### **3. Password Reset Delegation**

Administrators can delegate password-reset permissions to IT support
users.

This allows them to:

-   Reset passwords for users within the delegated OU.
-   Help users who have forgotten their passwords.
-   Perform support tasks without full administrative privileges.

### **4. Active Directory PowerShell Commands**

**Reset a user's password**

    Set-ADAccountPassword username -Reset -NewPassword (Read-Host -AsSecureString -Prompt 'New Password')

**Force a user to change their password at next login**

    Set-ADUser -ChangePasswordAtLogon $true -Identity username

Remember: Delegation follows the principle of **least privilege** ---
users should only receive the permissions they need to perform their
tasks.

## **Active Directory -- Organizing Machines**

By default, computers that join an Active Directory domain (except
Domain Controllers) are placed in the **Computers** container.

Keeping all computers in one container is not ideal because workstations
and servers have different security and management requirements.

### **1. Types of Machines in a Domain**

-   **Workstations:** Desktop computers and laptops used by employees
    for daily work. Privileged accounts should not normally log in to
    these devices.

-   **Servers:** Computers that provide services, applications or
    resources to users and other systems.

-   **Domain Controllers (DCs):** Servers that manage the domain,
    authentication and Active Directory. They are highly sensitive
    because they hold critical domain information.

### **2. Organizing Computers Using OUs**

Administrators can create separate OUs to organize devices based on
their purpose.

-   **Workstations OU** → Employee desktops and laptops.

-   **Servers OU** → Servers.

-   **Domain Controllers OU** → Domain Controllers (created by Windows
    by default).

### **3. Why Separate Them?**

-   Apply different Group Policies (GPOs).

-   Improve security management.

-   Manage devices more easily.

-   Apply different restrictions to workstations and servers.

-   Reduce security risks through proper organization.

**Remember:** Organizing computers into separate OUs allows
administrators to apply different security policies and configurations
depending on the device's role.

# **GPO -- Practical Implementation Guide**

## **1. Open Group Policy Management**

1.  Log in to the Domain Controller.

2.  Open the Start menu.

3.  Search for **Group Policy Management**.

4.  Open the tool.

5.  Expand **Forest → Domains → Your Domain**.

## **2. Practical 01 -- Restrict Control Panel Access**

User Configuration

**Objective:** Block non-IT users from accessing Control Panel and PC
Settings.

**Step 1 -- Create a new GPO**

1.  Expand your domain.

2.  Right-click **Group Policy Objects**.

3.  Select **New**.

4.  Enter the name: `Restrict Control Panel Access`.

5.  Click OK.

**Step 2 -- Edit the GPO**

1.  Find the newly created GPO.

2.  Right-click it.

3.  Select **Edit**.

**Step 3 -- Configure the policy**

Navigate to:

    User Configuration
      → Policies
        → Administrative Templates
          → Control Panel

1.  Find **Prohibit Access to Control Panel and PC settings**.

2.  Double-click it.

3.  Select **Enabled**.

4.  Click Apply → OK.

**Step 4 -- Link the GPO**

1.  Return to Group Policy Management.

2.  Find your newly created GPO under Group Policy Objects.

3.  Drag it to the following OUs:

    -   Marketing

    -   Management

    -   Sales

This applies the policy to users in those OUs. IT users are not
included.

**Step 5 -- Update and verify**

On the target computer, run:

    gpupdate /force

Try opening Control Panel to verify that access is blocked.

## **3. Practical 02 -- Auto Lock Screen**

Computer Configuration

**Objective:** Automatically lock workstations and servers after 5
minutes of inactivity.

**Step 1 -- Create a new GPO**

1.  Right-click **Group Policy Objects**.

2.  Select **New**.

3.  Enter the name: `Auto Lock Screen`.

4.  Click OK.

**Step 2 -- Edit the GPO**

1.  Find `Auto Lock Screen`.

2.  Right-click it.

3.  Select **Edit**.

**Step 3 -- Configure the policy**

Navigate to:

    Computer Configuration
      → Policies
        → Windows Settings
          → Security Settings
            → Local Policies
              → Security Options

1.  Find **Interactive logon: Machine inactivity limit**.

2.  Double-click it.

3.  Enable the policy or configure its value.

4.  Set the value to `300 seconds` (5 minutes).

5.  Click Apply → OK.

**Step 4 -- Link the GPO**

1.  Return to Group Policy Management.

2.  Find `Auto Lock Screen` under Group Policy Objects.

3.  Drag it to the root domain (`thm.local`).

The policy will be inherited by child OUs containing computers,
including Workstations, Servers and Domain Controllers, subject to
normal GPO processing and filtering.

**Step 5 -- Update and verify**

Run this command on the target computer:

    gpupdate /force

Leave the computer inactive for 5 minutes and verify that the session
locks.

## **4. Useful Commands for GPO Practical Work**

  Command                     Purpose
  --------------------------- --------------------------
  `gpupdate /force`           Force policy update
  `gpresult /r`               Display applied policies
  `gpresult /h report.html`   Generate GPO report

## **5. Practical Workflow -- Quick Revision**

1.  **Open Group Policy Management**

2.  **Create a new GPO** under Group Policy Objects

3.  **Right-click → Edit**

4.  **Navigate to the required policy setting**

5.  **Configure and enable the policy**

6.  **Link the GPO** to the required OU or domain

7.  **Run gpupdate /force**

8.  **Verify the policy** using gpresult or practical testing

**Important:** Creating a GPO alone does not apply it. You must link it
to the correct OU or domain for it to take effect.

# **Windows Domain Authentication -- Kerberos & NetNTLM**

## **1. Authentication Protocols**

Windows domains mainly use two authentication protocols:

-   **Kerberos:** Modern and default authentication protocol in Windows
    domains. Uses tickets.

-   **NetNTLM:** Older authentication protocol that uses a
    challenge-response mechanism. Kept for compatibility.

## **2. Kerberos Authentication**

Kerberos is a ticket-based authentication protocol. It allows users to
access network services without entering their password every time.

**Authentication process:**

1.  User logs in with domain credentials.

2.  KDC verifies the user's identity and issues a **TGT (Ticket Granting
    Ticket)**.

3.  User uses the TGT to request a **TGS (Service Ticket)** for a
    specific service.

4.  User sends the TGS to the target service.

5.  The service validates the ticket and grants access if authorized.

### **Important Terms**

  Term          Meaning
  ------------- -------------------------------------------------------
  KDC           Key Distribution Center -- manages and issues tickets
  TGT           Ticket used to request other tickets
  TGS           Ticket used to access a specific service
  SPN           Service Principal Name -- identifies a service
  Session Key   Secret key used to secure communication
  krbtgt        Special AD account whose key encrypts TGTs

Remember: TGT = Request tickets. TGS = Access a specific service.

## **3. NetNTLM Authentication**

NetNTLM uses a **Challenge--Response mechanism** to authenticate users.

**Authentication process:**

1.  Client requests access to a server.

2.  Server sends a random challenge.

3.  Client uses its NTLM password hash and the challenge to generate a
    response.

4.  Server forwards the challenge and response to the Domain Controller.

5.  DC verifies the response.

6.  Server allows or denies access.

-   Actual passwords are not transmitted over the network.

-   For domain accounts, the Domain Controller verifies authentication.

-   For local accounts, the server can verify authentication using its
    local SAM database.

## **4. Kerberos vs NetNTLM**

  Kerberos                            NetNTLM
  ----------------------------------- -----------------------------------
  Ticket-based authentication         Challenge-response authentication
  Uses TGT and TGS                    Uses challenge and response
  Default in modern Windows domains   Legacy compatibility protocol
  Uses KDC                            Uses DC for domain authentication

## **5. Related Security Attacks**

  -----------------------------------------------------------------------
  Attack                              Simple meaning
  ----------------------------------- -----------------------------------
  Kerberoasting                       Targets Kerberos service tickets
                                      for offline password cracking

  Pass-the-Hash                       Uses a password hash to
                                      authenticate without knowing the
                                      original password

  NTLM Relay                          Relays NTLM authentication messages
                                      to another service
  -----------------------------------------------------------------------

**Quick Revision**

-   Kerberos = Ticket-based authentication.

-   NetNTLM = Challenge-response authentication.

-   TGT = Ticket Granting Ticket.

-   TGS = Ticket for a specific service.

-   KDC = Issues Kerberos tickets.

-   SPN = Identifies a network service.

-   krbtgt = Special account used to protect TGTs.

# **Active Directory -- Trees, Forests & Trust Relationships**

## **1. Trees**

A **Tree** is a group of multiple Active Directory domains that share
the same namespace.

It allows an organization to manage different branches or locations
separately.

**Example:**

A company has two branches:

-   UK → `uk.thm.local`

-   US → `us.thm.local`

Both belong to the parent domain `thm.local`.

**Key points:**

-   Each domain can have its own Domain Controller.

-   Each domain can manage its own users and computers.

-   Each domain can have its own policies.

-   Domain Admins manage their respective domains.

## **2. Forests**

A **Forest** is a collection of multiple domain trees that can have
different namespaces.

It allows different organizations or companies to operate within a
shared Active Directory environment.

**Example:**

-   Company A → `thm.local`

-   Company B → `mht.local`

Both domain trees can belong to the same forest.

**Key points:**

-   A forest can contain multiple trees.

-   Trees can have different domain names.

-   Domains within a forest share a common AD structure and
    configuration.

-   Enterprise Admins have administrative privileges across the forest.

## **3. Trust Relationships**

A **Trust Relationship** allows users from one domain to access
resources in another domain, provided they have the required
permissions.

**Example:**

A user from the THM UK domain needs to access a shared folder in the MHT
EU domain.

A trust relationship allows the cross-domain authentication and access
process.

### **Types of Trust Relationships**

**1. One-Way Trust**

One domain trusts another domain.

Example:

-   Domain A trusts Domain B.

-   Users from Domain B can be authorized to access resources in Domain
    A.

-   The reverse is not automatically allowed.

**2. Two-Way Trust**

Both domains trust each other.

-   Users from Domain A can be authorized to access resources in Domain
    B.

-   Users from Domain B can be authorized to access resources in Domain
    A.

### **Important Terms**

  Term                Meaning
  ------------------- ---------------------------------------------
  Tree                Multiple domains sharing the same namespace
  Forest              Collection of domain trees
  Trust               Allows cross-domain access when authorized
  Domain Admins       Administrate their own domain
  Enterprise Admins   Administrate the entire forest

**Quick Revision**

-   **Tree** = Domains with the same namespace.

-   **Forest** = Multiple domain trees, potentially with different
    namespaces.

-   **One-Way Trust** = One domain trusts another.

-   **Two-Way Trust** = Both domains trust each other.

-   **Enterprise Admins** = Forest-wide administrative privileges.

Important: A trust relationship does not automatically give users access
to every resource. Permissions must still be assigned.

# **Windows Troubleshooting & Monitoring Tools**

## **1. Resource Monitor (**`resmon`**)**

Used to monitor real-time resource usage by individual processes.

-   **CPU:** Processor usage.

-   **Memory:** RAM usage.

-   **Disk:** Read/write activity and disk queue length.

-   **Network:** Network activity and connections.

**Use:** Identify which application is consuming high disk or network
resources.

    resmon

## **2. System Information (**`msinfo32`**)**

Displays detailed hardware and software information.

-   Processor details.

-   Installed RAM.

-   Hardware components.

-   Device drivers.

-   System configuration.

**Use:** Troubleshoot hardware and system configuration.

    msinfo32

## **3. Performance Monitor (**`perfmon`**)**

Used to monitor and analyze system performance using performance
counters.

-   CPU utilization.

-   Memory usage.

-   Disk activity.

-   Network performance.

-   Process performance.

**Use:** Collect performance data and identify long-term performance
issues.

    perfmon

## **4. Task Manager (**`taskmgr`**)**

Used to monitor running applications and processes.

-   CPU usage.

-   Memory usage.

-   Disk usage.

-   Network usage.

-   Running processes.

**Use:** Quickly identify applications consuming high system resources.

    taskmgr

## **5. IP Configuration (**`ipconfig /all`**)**

Displays detailed network adapter configuration.

-   IP address.

-   Subnet mask.

-   Default gateway.

-   DNS servers.

-   MAC address.

-   DHCP configuration.

**Use:** Troubleshoot network configuration and connectivity issues.

    ipconfig /all

## **Quick Revision**

  Tool                  Main Purpose
  --------------------- ---------------------------------------
  Resource Monitor      Real-time process resource monitoring
  System Information    Hardware and software details
  Performance Monitor   Detailed performance analysis
  Task Manager          Running processes and resource usage
  ipconfig /all         Network configuration

Exam Tip

-   High disk/network activity → **Resource Monitor**

-   Hardware information → **msinfo32**

-   Long-term performance analysis → **perfmon**

-   Check running processes → **Task Manager**

-   Check IP and DNS configuration → **ipconfig /all**
