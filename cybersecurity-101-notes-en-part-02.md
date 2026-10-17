# Cybersecurity 101 Notes — Part 02

> **Source:** TryHackMe — Cyber Security 101 / Windows Fundamentals and Active Directory Basics  
> **Format:** GitHub-friendly Markdown  
> **Images:** Image links are preserved where present. You can download and add the images yourself later.

## Table of Contents

- [Windows Fundamentals 1](#windows-fundamentals-1)
- [Windows Fundamentals 2](#windows-fundamentals-2)
- [Windows Fundamentals 3](#windows-fundamentals-3)
- [Active Directory Basics](#active-directory-basics)

---

# Windows Fundamentals 1

**Platform:** TryHackMe (Cyber Security 101 path)  
**VM / Lab:** Browser-based modules  
**Time spent:** 30 minutes

## Objective

In Part 1 of the Windows Fundamentals module, we learn about the NTFS file system, UAC, and related Windows concepts.

## Key Concepts Covered

### 1. Windows File System (NTFS Overview)

- NTFS replaced older file systems such as FAT16, FAT32, and HPFS.
- FAT is still used on USB flash drives and memory cards.
- NTFS can automatically repair files and directories by using information stored in logs.
- Benefits of NTFS include:
  - Supports files larger than 4 GB.
  - Allows specific permissions to be assigned to files and directories.
  - Supports file and directory compression.
  - Includes the Encrypting File System (EFS) to help protect data.

### 2. NTFS Permissions for Files and Folders

Permission types include:

- Full Control
- Modify
- Read & Execute
- List Folder Contents
- Read
- Write

The [image](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/ntfs_permissions.png) illustrates how each permission applies to files and folders.

### 3. Alternate Data Streams (ADS) in NTFS

- ADS allows files to contain multiple data streams (the primary stream is `$DATA`).
- Windows Explorer does not display ADS by default; PowerShell or third-party applications are required to inspect them.

### 4. Windows Directory and Environment Variables

- `C:\Windows` is the standard location of the Windows operating system, although Windows can also be installed on another drive or directory.
- **System environment variables** help locate system directories regardless of their actual paths.
- `%windir%` is an environment variable that points to the Windows directory.
- Environment variables store operating-system-related information, such as:
  - OS path
  - Number of processors
  - Temporary directory locations

### 5. [System32 Directory](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/system_32.jpg)

- Contains essential system files required for Windows to operate.
- Deleting files here can break the operating system.
- Many tools discussed in Windows Fundamentals are located in System32.
- It is a core part of the operating system and is not intended for casual modification.

### 6. Types of User Accounts in Windows

The two main types of local user accounts are:

- **Administrator:** Can add or remove users, change groups and settings, and install or uninstall software.
- **Standard User:** Can modify their own files and folders but cannot make system-level changes without authorization.

### 7. User Account Control (UAC)

- Many users sign in with local administrator accounts, which can allow system-level changes.
- Working with elevated privileges increases risk because attackers may abuse administrative access.
- UAC was introduced in Windows Vista to reduce this risk.
- UAC provides the following protections:
  - Even administrator accounts do not run with elevated privileges by default.
  - When a task requires higher privileges, the system asks the user for confirmation.
- When installing software, Windows may display the [UAC shield](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/UAC_shield.png) and request [administrator credentials](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/UAC_admin_creds.png).

### 8. Task Manager

The [Task Manager](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/task_manager.png) displays real-time information, including:

- Running applications
- Background processes
- CPU and RAM usage

It is useful for diagnosing, stopping, and monitoring system tasks and processes.

## Learning and Reflections

- Learned about NTFS and its permissions.
- Learned about System32 and environment variables.
- Learned how UAC helps avoid unnecessary privileged access.
- Learned about Task Manager and how it is used.

---

# Windows Fundamentals 2

**Platform:** TryHackMe (Cyber Security 101 path)  
**VM / Lab:** Browser-based modules  
**Time spent:** 20 minutes

## Objective

In Part 2 of the Windows Fundamentals module, we learn about System Configuration, Resource Monitor, and related tools.

## Key Concepts Covered

### 1. System Configuration (`msconfig`)

- Used for advanced diagnostics and troubleshooting startup problems.
- Starting it requires **local administrator** privileges.
- It can be opened from the Start menu or by running `msconfig`.

System Configuration tabs:

1. **[General tab](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/general_tab.png)**
   - Selects the startup mode:
     - **Normal startup:** Loads all device drivers and services.
     - **Diagnostic startup:** Loads only basic devices and services.
     - **Selective startup:** Lets you customize what loads (system services, startup items, and boot configuration).
2. **[Boot tab](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/boot_tab.png)**
   - Configures boot options such as Safe boot, No GUI boot, Boot log, and timeout settings.
3. **[Services tab](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/service_tab.png)**
   - Lists system services, including their names, manufacturers, statuses, and disabled dates.
   - Includes an option to hide Microsoft services to help avoid disabling critical components.
4. **[Tools tab](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/tool_tab.png)**
   - Launches built-in Windows tools, such as Command Prompt and Event Viewer.
   - Displays the tool name, description, and executable path (for example, `C:\Windows\System32\cmd.exe`).

### 2. [Resource Monitor](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/resource_monitor.png)

- A powerful diagnostic tool for advanced troubleshooting.
- Shows per-process and overall usage of:
  - CPU
  - Memory
  - Disk
  - Network
- Key features include:
  - Showing which processes use file handles and modules.
  - Filtering by process, application, or service.
  - Starting, stopping, pausing, or resuming services.

### 3. Windows Command Prompt

- Command Prompt (`cmd`) allows users to interact directly with the operating system through text commands.
- It remains useful for system information, troubleshooting, and automation.
- Common commands:
  - `hostname` — Displays the computer's name.
  - `whoami` — Displays the currently logged-in user.
  - `ipconfig` — Displays network configuration.
- Most commands support `/?` to display their syntax and help information.

### 4. [Windows Registry](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/registry_editor.png)

- Can be opened through Start/Search by running `regedit`.
- The Windows Registry is a hierarchical database used to store:
  - Operating system configuration settings
  - User preferences
  - Application information
  - Hardware configurations
- Editing the Registry is an advanced and risky task: incorrect changes can affect system functionality.
- Main root keys:
  - `HKEY_CLASSES_ROOT` — File-type associations.
  - `HKEY_CURRENT_USER` — Settings for the current user.
  - `HKEY_LOCAL_MACHINE` — System-wide settings.
  - `HKEY_USERS` — All user profiles.
  - `HKEY_CURRENT_CONFIG` — Hardware profile information.

## Learning and Reflections

- Learned about System Configuration.
- Learned about Resource Monitor.
- Learned about Command Prompt and various commands.
- Learned about the Windows Registry and its main root keys.

---

# Windows Fundamentals 3

**Platform:** TryHackMe (Windows Fundamentals series)  
**VM / Lab:** Windows virtual machine (VM)  
**Time spent:** Approximately 10–15 minutes

## Objective

This module focuses on built-in security tools in Microsoft Windows. Its goal is to explain how key mechanisms designed to protect Windows devices work, including **Windows Update**, **Windows Security**, **Microsoft Defender**, **Firewall**, **TPM**, **BitLocker**, and **Volume Shadow Copy Service (VSS)**.

## Key Concepts

### 1. Windows Updates

Keeping Windows updated is critical for fixing security vulnerabilities.

- Microsoft usually releases updates on the second Tuesday of each month (**Patch Tuesday**), although urgent situations can result in exceptions.
- **Definition updates** are regularly downloaded updates for virus and malware definitions (signatures).

### 2. Windows Security & Microsoft Defender

Windows Security is a unified dashboard that visually displays the device's security and health status using green, yellow, and red indicators.

- **Virus & Threat Protection:** Manages the built-in **Microsoft Defender** scanner.
- **Real-time protection:** Provides real-time protection against malicious code. When disabled, the system is at risk.
- **Scan options:** Quick, Full, Custom, and Offline scan modes are available.

### 3. Firewall & Network Protection

The built-in Windows firewall uses three main profiles to manage network traffic:

- **Domain network:** For corporate/domain environments.
- **Private network:** For home or trusted internal networks.
- **Public network:** For public Wi-Fi networks, such as those in airports and cafés.

### 4. App & Browser Control

This area includes two main protection mechanisms:

- **Microsoft Defender SmartScreen:** Checks unrecognized applications and files downloaded from the web.
- **Exploit Protection:** Provides built-in protection against the exploitation of system vulnerabilities.

### 5. Device Security & Encryption (Device Security & BitLocker)

- **Core Isolation (Memory Integrity):** Uses Hyper-V virtualization technology to isolate operating-system kernel processes in memory.
- **TPM (Trusted Platform Module):** A dedicated hardware security chip that performs cryptographic operations.
- **BitLocker:** Provides full-disk encryption. If the system does not have a TPM chip (version 1.2 or later), a **USB startup key** is required during boot.

### 6. Volume Shadow Copy Service (VSS)

VSS is a coordination service that allows data to be backed up even while applications are running or the system is online. Malware such as ransomware may try to delete VSS copies, so keeping offline backups is recommended.

## Task Questions and Answers

- **Task 2 (Windows Updates):** On what date were the two definition updates installed on the provided VM?  
  **Answer:** `5/3/2021`
- **Task 3 (Windows Security):** Which area in the displayed dashboard requires immediate attention?  
  **Answer:** `Virus & threat protection`
- **Task 4 (Virus & Threat Protection):** Which specific mode is turned off and which Windows recommends enabling?  
  **Answer:** `Real-time protection`
- **Task 5 (Firewall & Network Protection):** Which firewall profile is active when connecting to an airport's Wi-Fi network?  
  **Answer:** `Public network`
- **Task 7 (Device Security):** What does TPM stand for?  
  **Answer:** `Trusted Platform Module`
- **Task 8 (BitLocker):** What must a user enter on computers WITHOUT TPM version 1.2 or later?  
  **Answer:** `USB startup key`
- **Task 9 (VSS):** What does the acronym VSS stand for?  
  **Answer:** `Volume Shadow Copy Service`

## Learning and Reflections

- Became familiar with the main structure of Windows' built-in security dashboard (Windows Security).
- Learned how **BitLocker** encryption works with the **TPM** hardware chip and that a USB key is required when TPM is unavailable.
- Learned the role of **VSS** in data backups and why offline backups are important against malware.

---

# Active Directory Basics

**Platform:** TryHackMe (Cyber Security 101 path)  
**VM / Lab:** Browser-based modules  
**Time spent:** 30 minutes

## Objective

This module introduces the core concepts and functionality provided by Active Directory.

## Key Concepts Covered

### 1. Windows Domains & Active Directory (AD)

- A Windows domain is a centralized network structure used to manage users, computers, and resources within an organization.
- Instead of configuring every machine individually, administrators use a **Domain Controller (DC)** to manage everything from one place.
- The **Active Directory (AD)** service runs on the DC and acts as a central repository for:
  - User accounts
  - Machine accounts
  - Security policies
  - Group memberships
- Benefits of using a Windows domain:
  - All users and computers are managed through AD.
  - Reduces manual configuration and improves scalability.
  - Provides consistent access control and compliance.

### 2. [Active Directory Domain Services (AD DS)](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/Users_AD.png)

The main objects in AD include:

- **Users:**
  - Represent individuals who need access to resources.
  - Can be grouped and assigned permissions.
- **Machines:**
  - Every computer in the domain is treated as an object.
  - A machine named `CORE1` will have an account named `CORE1$`.
- **Groups:**
  - Collections of users or machines.
  - Used to simplify permission management.

### 3. [Organizational Units (OUs)](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/Organization_units.png)

- OUs are containers used to organize AD objects (users, computers, and groups).
- A company might have OUs for Administration, Marketing, R&D, Sales, and so on.
- Different Group Policies can be applied to each OU for customized configurations.

### 4. Default Containers in AD

- **Builtin:** Default groups (for example, Administrators and Users).
- **Computers:** Newly domain-joined machines are placed here by default.
- **Domain Controllers:** Contains all DCs in the network.
- **Users:** Default users and groups for domain access.
- **Managed Service Accounts:** Used by services running in the domain.

### 5. Delegation in Active Directory

- Delegation is the process of granting non-domain-administrator users specific administrative privileges over certain parts of the **Active Directory** structure, usually over Organizational Units.
- It enables granular administration without granting full domain-level access.
- It is commonly used to empower IT support staff or department managers to manage their own teams.

**How to delegate control:**

1. Open Active Directory Users and Computers.
2. [Right-click the target OU.](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/delegate_right_click.png)
3. Select [“Delegate Control”.](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/delegate_right_click.png)
4. A [wizard appears.](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/delegate_wizard.png)
5. Use the wizard to:
   - Select a user or group.
   - Select specific tasks (such as resetting passwords or creating/deleting user accounts).
   - Apply the settings and finish.

### 6. Managing Computers in Active Directory

- When a computer joins the domain, it is automatically placed in the **Computers** container.
- This includes:
  - Workstations
  - Laptops
  - Servers
- Domain Controllers (DCs) are placed in a separate container called **Domain Controllers**.

**Organizing computers into OUs:**

- The Computers container is not an Organizational Unit (OU), so Group Policies cannot be applied directly to it.
- To manage devices effectively, especially in large environments, it is best to create dedicated OUs for different device types.

**[Recommended OU structure](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/OU_structure.jpg)**

- Organizing devices into OUs enables targeted policy application and easier management.
- These OUs are created directly under the domain for clarity and manageability: `itconnect.local`.
- Settings can be applied by linking Group Policies to each OU.

### 7. Group Policy Objects (GPOs) in Active Directory

- GPOs are collections of settings that control user and computer behavior in a Windows domain.
- They allow administrators to apply policies across the network without manually configuring every machine.
- GPOs can be applied to:
  - Domains
  - Organizational Units
  - Groups
  - Individual users or computers
- The tool used to manage Group Policy is [Group Policy Management](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/group_policy_management.png).
- GPOs are created under the Group Policy Objects container.
- They are then linked to specific OUs or domains.
- Examples:
  - `Default Domain Policy` — Linked to the entire domain.
  - `Default Domain Controllers Policy` — Linked to the Domain Controllers OU.
  - `Sales GPO` — Linked to the Sales OU.

### 8. [GPO Scope and Settings](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/scope_GPO.png)

Each GPO has two main configuration areas:

1. **Computer Configuration:** Applies settings to machines (security policies, software installation).
2. **User Configuration:** Applies settings to user accounts (desktop restrictions, logon scripts).

- The **Settings** tab in GPMC shows all active policies within a GPO.
- **Security Filtering** can restrict GPO application to specific users or groups.

### 9. Authentication in Windows Domains

Windows domains rely on secure authentication protocols to verify user identities and grant access to services. The two main protocols are:

#### Kerberos Authentication (Default Protocol)

- Kerberos is the standard and preferred authentication method in modern Windows domains. It uses a **ticket-based system** to authenticate users securely without transmitting passwords over the network.

**Kerberos workflow:**

1. **[Initial logon](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/kerberos_initial_login.png)**
   - The user sends their **username and timestamp**, encrypted with a key, to the **Key Distribution Center (KDC)**.
   - The KDC (running on the Domain Controller) verifies the credentials and returns a **Ticket-Granting Ticket (TGT)** encrypted with the **krbtgt hash**, and a **Session Key** encrypted with the user's password hash.
2. **[Requesting access to a service](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/kerberos_request_TGS.png)**
   - The user sends the **TGT**, **Session Key**, a new (encrypted) timestamp, and the requested service's **Service Principal Name (SPN)** to the KDC.
   - The KDC returns a **Ticket-Granting Service (TGS) ticket** encrypted with the service owner's hash and a **Service Session Key** for secure communication with the service.
3. **[Accessing the service](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/kerberos_access_service.png)**
   - The user presents the TGS ticket and Service Session Key to the target service.
   - The service decrypts the TGS using its own password hash and validates the session key.
   - If it is valid, access is granted.
4. **Security features of the Kerberos workflow**
   - Passwords are never transmitted.
   - Tickets are time-bound and encrypted.
   - Kerberos supports mutual authentication (both client and server verify each other).

#### NTLM/NetNTLM Authentication (Legacy Protocols)

- NTLM is used for **backward compatibility**.
- It is still supported in environments where Kerberos is not feasible (workgroups and legacy systems).
- NTLM is considered less secure and should be avoided when possible.

**[NetNTLM workflow](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/NTLM_workflow.png)**

1. **Client → Server:** Sends an authentication request.
2. **Server → Client:** Sends a challenge (a random number).
3. **Client → Server:** Responds with a hash of the challenge combined with the NTLM password hash.
4. **Server → Domain Controller:** Forwards the challenge and response.
5. **Domain Controller:** Recomputes the expected response using the stored NTLM hash.
6. **Server:** Compares the responses. If they match, authentication succeeds.

### 10. Trees, Forests, and Trusts in Active Directory

- A single domain may be sufficient for a small company.
- As businesses expand across countries, their legal, operational, and IT needs can differ.
- Separate domains allow:
  - Independent **Group Policies**.
  - Localized **administrative control**.
  - Better **security boundaries**.

#### [Trees (Hierarchical Domain Structure)](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/trees.png)

- A tree is a collection of domains that share a common namespace.
- Example:
  - Root domain: `thm.local`
  - Subdomains: `uk.thm.local`, `us.thm.local`
- Each domain has its own Domain Controller (DC):
  - `DC-ROOT` for `thm.local`
  - `DC-UK` for `uk.thm.local`
  - `DC-US` for `us.thm.local`
  - These are example domains.
- Administrative roles in trees:
  - **Domain Admins:** Full control over their own domain.
  - **Enterprise Admins:** Full control over all domains in the forest.

#### [Forests (Multiple Trees in an Enterprise)](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/forests.png)

- A forest is a collection of one or more domain trees that do not share the same namespace.
- This is common in mergers or large enterprises with different IT infrastructures.
- Examples:
  - Tree 1: `thm.local`, `uk.thm.local`, `us.thm.local`
  - Tree 2: `mht.local`, `eu.mht.local`, `asia.mht.local`

#### [Trust Relationships](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/trust.png)

- Trusts allow users in one domain to access resources in another domain.
- Types of trust:
  - **One-way trust:** Domain A trusts Domain B → users from B can access A, but not the other way around.
  - **Two-way trust:** Mutual trust → users from both domains can access each other's resources, subject to permissions.
  - **Default trusts:** Domains in the same tree or forest automatically establish two-way trusts.
- **A trust does not automatically grant access.** Users must still be explicitly permitted to access specific resources.

## Learning and Reflections

- Learned about Windows domains and Active Directory.
- Learned about OUs and default containers.
- Learned about two different authentication methods in Windows domains.
- Learned about trees, forests, and trust relationships.
