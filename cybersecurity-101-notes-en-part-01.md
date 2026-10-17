# TryHackMe Cyber Security 101 — Study Notes

> English translation of the original study notes. Commands, technical identifiers, and source links are preserved. Add screenshots and images manually where needed.

## Related Resources

- [TryHackMe — HH 2026](https://app.notion.com/p/THM-HH-2026-3acf9a50a539806782e5eec874bab9fd?pvs=21)
- [HTB Academy](https://app.notion.com/p/HTB-ACADEMY-3b5f9a50a539801fa599d5a2d71aebaa?pvs=21)
- [The Scout Mindset](https://app.notion.com/p/The-Scout-Mindset-3cbf9a50a53980fba4e6e55e88c9d01c?pvs=21)

---

# 1. Introduction to Offensive Security

**Platform:** TryHackMe (Cyber Security 101 path)  
**VM / Lab:** Browser-based modules  
**Time spent:** 5 minutes

## Objective

Begin learning how to hack a website legally in a safe environment and experience the work of an ethical hacker.

## Key Concepts Covered

### 1. What is offensive security?

- It is the practice of simulating hacker behaviour to identify system vulnerabilities.
- It involves gaining access to systems, exploiting mistakes, and finding weaknesses.
- The goal is to understand attackers' tactics in order to strengthen defences.

## Learning and Reflections

- I learned about offensive security.

---

# 2. Introduction to Defensive Security

**Platform:** TryHackMe (Cyber Security 101 path)  
**VM / Lab:** Browser-based modules  
**Time spent:** 15 minutes

## Objective

Learn about defensive security and related topics such as threat intelligence, SOC operations, DFIR, malware analysis, and SIEM.

## Key Concepts Covered

### 1. What is defensive security (the Blue Team)?

- It focuses on protecting an organisation's IT infrastructure.
- Its main responsibilities include:
  - Preventing intrusions.
  - Detecting intrusions.
  - Responding effectively to intrusions.

### 2. What is a SOC (Security Operations Centre)?

- A team of cybersecurity professionals who monitor networks and systems.
- They detect and respond to malicious cybersecurity incidents promptly.
- The main areas of SOC work include:
  - Keeping up to date with industry threats and vulnerabilities.
  - Monitoring compliance with the organisation's security policies.
  - Investigating anomalies to maintain trust and integrity.
  - Responding quickly to minimise damage.

### 3. What is digital forensics?

- It applies traditional forensic methods to digital devices.
- It focuses on preserving and analysing digital evidence during investigations, such as investigations into data breaches.
- Major sources of digital evidence include:
  1. **File system:** Low-level storage analysis can reveal created, overwritten, and deleted files.
  2. **System memory:** Collects volatile data from programs running in memory.
  3. **System logs:** Track system activity; traces may remain even after attempts to delete them.
  4. **Network logs:** Track traffic to identify signs of an attack and understand its scope.

### 4. What is incident response?

- A structured approach to managing cybersecurity incidents, such as intrusions or data breaches.
- Its goal is to minimise damage, contain threats, and recover quickly.
- The four main stages of incident response are:
  1. **Preparation**
     - Develop policies, procedures, and training.
     - Implement security measures.
  2. **Detection and analysis**
     - Monitor systems and networks for suspicious activity.
     - Analyse events to confirm incidents.
  3. **Containment, eradication, and recovery**
     - Limit the impact of the incident.
     - Remove the threats.
     - Restore affected services and systems.
  4. **Post-incident activity**
     - Review the incident and the response.
     - Update policies and training based on lessons learned.

## Learning and Reflections

- I spent a short time learning about defensive security.
- I learned about SOCs and their roles.
- I learned how digital devices are examined through digital forensics.
- I learned how responses to incidents can be handled effectively.

---

# 3. Search Skills

**Platform:** TryHackMe (Cyber Security 101 path)  
**VM / Lab:** Browser-based modules  
**Time spent:** 15 minutes

## Objective

Learn to search the internet efficiently and use specialised search engines and technical documentation.

## Key Concepts Covered

### 1. Overview of search engines

- Search engines help find information on the internet.
- Search operators improve the precision and relevance of results.
- Useful Google search operators:

  1. **`"exact phrase"`**
     - Finds pages containing an exact phrase.
     - Example: `"passive reconnaissance"`
  2. **`site:`**
     - Restricts results to a particular website or domain.
     - Example: `site:TryHackMe.com successstories`
  3. **Minus sign (`-`)**
     - Excludes specific terms from the results.
     - Example: `pyramids -tour -tourism`
  4. **`filetype:`**
     - Searches for specific file formats.
     - Example: `filetype:pdf cyber security`

### 2. What is [Shodan](https://www.shodan.io/)?

- A search engine for internet-connected devices.
- It can be used to find servers, network equipment, ICS systems, and IoT devices.
- It helps identify exposed systems and outdated software versions.
- Example search: [Apache 2.4.1](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/shodan_apache_search.jpg)
  - **Total results:** 13,493 servers running Apache 2.4.1.
  - **Top countries**, for example:
    - **Japan:** 3,350
    - **Singapore:** 3,107
    - And others.

### 3. What is [Censys](https://search.censys.io/)?

- A search engine for internet-connected hosts, websites, certificates, and other assets.
- It is similar to Shodan, but focuses more on internet-wide scanning, auditing, and asset discovery.
- It is useful for:
  - Identifying open ports and services.
  - Tracking software versions across the web.
- Example search: [apache_2.4.1](https://github.com/FROSTmatic-hub/tryhackme-notes/blob/main/cybersecurity-101/images/censys_apache_search.png)
  - Returns hosts running Apache 2.4.1.
  - Results include:
    - IP addresses
    - Location (city and country)
    - Organisation
    - Running services, such as HTTP on port 80 and HTTPS on port 443

### 4. What is [VirusTotal](https://www.virustotal.com/gui/home/upload)?

- An online tool that scans files and URLs using multiple antivirus engines.
- It is useful for checking suspicious files and links before executing or sharing them.

### 5. What is [Have I Been Pwned (HIBP)](https://haveibeenpwned.com/)?

- A free service that checks whether an email address has appeared in data breaches.
- It helps users learn about compromised credentials and take appropriate action.

### 6. What is CVE?

- CVE stands for **Common Vulnerabilities and Exposures**.
- It provides standardised IDs for publicly known security flaws.
- It helps track and share vulnerability information across platforms and vendors.

### 7. What is the [Exploit Database](https://www.exploit-db.com/)?

- A public repository of known exploits for software vulnerabilities.
- It is used by ethical hackers, researchers, and penetration testers.
- It helps validate vulnerabilities and simulate real-world attacks in a lab environment.

## Learning and Reflections

- I learned about different search engines and search operators.
- I learned about Shodan.
- I learned about Censys.
- I learned about VirusTotal.
- I learned about HIBP.
- I learned about CVEs and the Exploit Database.

---

# 4. Linux Fundamentals — Part 1

**Platform:** TryHackMe (Pre Security path)  
**VM / Lab:** Browser-based modules  
**Time spent:** 20 minutes

## Objective

Begin learning the fundamentals of Linux. Learn to use some of the first essential commands in an interactive terminal.

## Key Concepts Covered

### 1. Introduction to Linux

- Linux is an open-source operating system used on servers, in hacking labs, and for development.
- It is valued for its flexibility, security, and command-line capabilities.

### 2. Background on Linux

- Linux powers websites, smart cars, point-of-sale (POS) systems, and industrial controllers.
- It is based on Unix and is available in many distributions, such as Ubuntu and Debian.

### 3. Running your first commands

| Command | Description |
|---|---|
| `echo "text"` | Prints text to the terminal. |
| `whoami` | Displays the currently logged-in user. |
| `ls` | Lists files in the current directory. |
| `cd foldername` | Changes directory. |
| `cat filename` | Displays a file's contents. |
| `pwd` | Prints the current working directory. |
| `find -name filename` | Searches for files by name. |
| `find -name "*.txt"` | Uses a wildcard to find all `.txt` files. |
| `grep "search_term" filename` | Searches files for a specific term. |

### 4. Introduction to shell operators

| Operator | Description |
|---|---|
| `&` | Runs a command in the background. |
| `&&` | Runs the second command only if the first succeeds. |
| `>` | Redirects output to a file, overwriting its existing contents. |
| `>>` | Appends output to a file, preserving existing contents. |

## Learning and Reflections

- I learned about Linux and its history.
- I learned various commands used to navigate the file system.
- I learned about shell operators.

---

# 5. Linux Fundamentals — Part 2

**Platform:** TryHackMe (Pre Security path)  
**VM / Lab:** Browser-based modules  
**Time spent:** 20 minutes

## Objective

Continue learning Linux by exploring how to connect to a Linux machine using SSH, use command options, and interact with the file system.

## Key Concepts Covered

### 1. Connecting to your Linux machine using SSH

- SSH (Secure Shell) is an encrypted protocol for remote access.
- The lesson demonstrates launching a Linux machine and the TryHackMe AttackBox.
- It shows how to connect using credentials, with a command such as `ssh tryhackme@<IP>`.

### 2. Introduction to flags and switches

- Command-line flags modify a command's behaviour. Example: `ls -als -l`.
- Help options and manual pages provide command documentation. The original note refers to `-help` and `man`.

### 3. More file-system interaction

- Create files and directories with commands such as `touch filename` and `mkdir foldername`.
- Remove files and directories with `rm` and `rm -r`.
- Copy and move files with `cp` and `mv`.
- Identify file types, including files without extensions, using `file filename`.

### 4. Permissions 101

- Linux file permissions are analysed for the user, group, and others: `rwx`.
- Use `ls -l` to view permission columns.
- The notes introduce switching users with `su` and `su -l`.

### 5. Common directories

- **`/etc`**: Contains system configuration files, including files such as `passwd`, `shadow`, and `sudoers`.
- **`/var`**: Stores variable data, such as logs and databases.
- **`/root`**: The root user's home directory.
- **`/tmp`**: Temporary storage that is cleared on reboot on some systems/configurations.

## Learning and Reflections

- I learned to access machines remotely using SSH.
- I learned about flags and switches.
- I learned about different users, groups, and permissions.

---

# 6. Linux Fundamentals — Part 3

**Platform:** TryHackMe (Pre Security path)  
**VM / Lab:** Browser-based modules  
**Time spent:** 18 minutes

## Objective

Improve Linux skills and gain practical familiarity with common utilities that can be used in everyday work.

## Key Concepts Covered

### 1. Terminal text editors

- Introduces text editors such as `nano` and `vim`.
- Demonstrates creating and saving files with a command such as `nano <filename>`.

### 2. Common and useful utilities

- `wget`: Downloads files over HTTP.
- `scp`: Securely transfers files between machines.
- `python3 -m http.server`: Demonstrates serving files over HTTP.

### 3. Processes 101

- Use `ps` and `ps aux` to inspect running processes.
- Introduces `top` for real-time process monitoring.
- Explains `kill` and the signals `SIGTERM`, `SIGKILL`, and `SIGSTOP`.
- Demonstrates foreground processes (`fg`) and background processes (`&`, `Ctrl+Z`).

### 4. Automation

- Introduces `cron` and `crontab -e` for scheduling tasks.
- Explains cron syntax and wildcards (`*`).
- Example: backing up files every 12 hours.

### 5. Package management

- Explains `apt`, repositories, and `sources.list`.
- Demonstrates GPG keys and adding third-party repositories.
- Shows how to install and remove packages such as Sublime Text.

### 6. Logs

- Reviews log directories and important logs, such as `/var/log`, `access.log`, and `error.log`.
- Uses tools such as `less` to inspect logs and review IP addresses and file-access information.

## Learning and Reflections

- I learned about different text editors in Linux.
- I learned how to monitor and terminate processes.
- I learned how to automate tasks using `cron`.
- I learned how to install packages using `apt`.
- I learned how to view log files for errors and access activity.
