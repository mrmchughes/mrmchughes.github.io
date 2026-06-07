---
publish: true
created: 2026-05-06
modified: 2026-05-08T16:07:13.395Z
---

# Vault Index — Starter Note Stubs

> Click any `[[Link]]` to create the note as a stub. Each section notes which template to apply when filling it in. Don't try to create every note now — most should be written from your own practice. This is a "is there a note here yet?" reference, not a to-do list.

## Template legend

The eight templates this vault uses, what they're for, and the frontmatter shape they enforce:

| Template | Used for | Key fields |
|----------|----------|------------|
| [[Technique-Template]] | Atomic actions you take during an engagement (most of the vault) | trigger, prerequisites, procedure, pivot, OPSEC |
| [[Tool-Template]] | One per tool — nmap, BloodHound, Impacket, etc. | flags table, common invocations, OPSEC, alternatives |
| [[Cheatsheet-Template]] | Quick-lookup reference; ports, defaults, command sheets | dense tables, minimal prose |
| [[CVE-Template]] | One per CVE you've actually used | affected versions, detection, exploitation, remediation |
| [[Payload-Template]] | Reusable payloads (revshells, web shells, encoded cmds) | payload body, listener setup, variables, variants |
| [[MOC-Template]] | Map of Content pages — navigation across techniques | decision flow, dataview queries, manual ordering |
| [[Cert-Roadmap-Template]] | One per cert you're targeting | required skills, lab progress, gaps, schedule |
| [[Box-Template]] | Per-box / per-engagement writeups | recon, IA, priv esc, lessons, new techniques |

**Templater shortcut:** if you're using Templater, you can configure folder templates so the correct one auto-applies when you create a note in each folder. Settings → Templater → Folder Templates → map each folder to its template. After that, you don't have to manually pick.

## Obsidian setup for clickable stubs

Default behavior: clicking a `[[link]]` creates the file in your vault root. Recommended workflow: Settings → Files and Links → "Default location for new notes" → "Same folder as current file." Then copy each section of this index into `_Index.md` files inside the relevant folders so clicked stubs land in the right place.

---

# 01-Methodology

## 01-Pre-Engagement

> Mixed: scoping/comms are techniques; ROE, engagement letters, and checklists are reference docs.

- [[Scoping]] — Technique
- [[Rules of Engagement]] — Cheatsheet
- [[Engagement Letter]] — Cheatsheet
- [[Client Communication]] — Technique
- [[Pre-Engagement Checklist]] — Cheatsheet

## 02-Reconnaissance — Passive

> All notes here use the **Technique** template.

- [[WHOIS Lookup]]
- [[DNS Records Enumeration]]
- [[Subdomain Enumeration Passive]]
- [[Certificate Transparency Search]]
- [[Google Dorking]]
- [[GitHub Recon]]
- [[Email-Harvesting]]
- [[Employee Enumeration]]
- [[Shodan Recon]]
- [[Wayback Machine Recon]]
- [[LinkedIn-OSINT]]
- [[Pastebin Search]]

## 02-Reconnaissance — Active

> All notes here use the **Technique** template.

- [[Host Discovery]]
- [[ARP-Discovery]]
- [[TCP-Port-Scan]]
- [[UDP Port Scan]]
- [[Service Version Detection]]
- [[OS Fingerprinting]]
- [[Subdomain Enumeration Active]]
- [[Vhost Enumeration]]
- [[Banner Grabbing]]

## 03-Enumeration

> All notes here use the **Technique** template.

- [[FTP Enumeration]]
- [[SSH Enumeration]]
- [[Telnet Enumeration]]
- [[SMTP Enumeration]]
- [[DNS Enumeration]]
- [[HTTP Enumeration]]
- [[POP3 Enumeration]]
- [[RPC Enumeration]]
- [[NetBIOS Enumeration]]
- [[IMAP Enumeration]]
- [[SNMP Enumeration]]
- [[LDAP Enumeration]]
- [[SMB Enumeration]]
- [[Kerberos Enumeration]]
- [[MSSQL Enumeration]]
- [[NFS Enumeration]]
- [[MySQL Enumeration]]
- [[PostgreSQL Enumeration]]
- [[RDP Enumeration]]
- [[WinRM-Enumeration]]
- [[Redis Enumeration]]
- [[MongoDB Enumeration]]
- [[IPMI Enumeration]]
- [[IKE Enumeration]]
- [[TFTP Enumeration]]
- [[NTP Enumeration]]
- [[VNC Enumeration]]
- [[Rsync-Enumeration]]

## 04-Vulnerability-Analysis

> All notes here use the **Technique** template.

- [[Searchsploit Workflow]]
- [[Version To CVE Mapping]]
- [[Nuclei Scanning]]
- [[Vulnerability Triage]]

## 05-Initial-Access

> All notes here use the **Technique** template.

- [[Default Credential Testing]]
- [[Password Spraying]]
- [[Credential Stuffing]]
- [[Credential Reuse]]
- [[Anonymous FTP Access]]
- [[SMB Null Session]]
- [[Web Shell Upload]]
- [[SSH Key Reuse]]
- [[Public Facing Exploit]]
- [[Phishing-Payload-Delivery]]
- [[Malicious Macro Document]]
- [[HTML Smuggling]]

## 06-Privilege-Escalation — Linux

> All notes here use the **Technique** template.

- [[Linpeas Execution]]
- [[Manual Linux Enumeration]]
- [[Sudo Misconfiguration]]
- [[SUID Binary Abuse]]
- [[GTFOBins Lookup]]
- [[Kernel Exploit Linux]]
- [[Cron Job Abuse]]
- [[Path Hijacking]]
- [[Capabilities Abuse]]
- [[Writable Etc Passwd]]
- [[Writable Etc Shadow]]
- [[NFS Root Squash Abuse]]
- [[Docker Group Escape]]
- [[LXD Group Escape]]
- [[Polkit CVE 2021 4034]] — Technique _(or CVE if focusing on the vuln itself)_
- [[DirtyPipe]] — Technique _(or CVE)_
- [[Wildcard Injection]]

## 06-Privilege-Escalation — Windows

> All notes here use the **Technique** template.

- [[Winpeas Execution]]
- [[Manual Windows Enumeration]]
- [[Unquoted-Service-Path]]
- [[Weak-Service-Permissions]]
- [[AlwaysInstallElevated]]
- [[SeImpersonatePrivilege-Abuse]]
- [[SeBackupPrivilege-Abuse]]
- [[SeRestorePrivilege-Abuse]]
- [[SeTakeOwnershipPrivilege-Abuse]]
- [[Dll Hijacking]]
- [[Stored Credentials Windows]]
- [[AutoLogon Registry]]
- [[Scheduled-Task-Abuse]]
- [[UAC-Bypass]]
- [[PrintNightmare]] — Technique _(or CVE)_
- [[Potato-Family-Exploits]]

## 06-Privilege-Escalation — Active-Directory

> All notes here use the **Technique** template.

- [[Kerberoasting]]
- [[AS-REP-Roasting]]
- [[Unconstrained-Delegation-Abuse]]
- [[Constrained-Delegation-Abuse]]
- [[Resource-Based-Constrained-Delegation]]
- [[ACL-Abuse-AD]]
- [[GenericAll-Abuse]]
- [[GenericWrite-Abuse]]
- [[WriteDACL-Abuse]]
- [[GPP-Password-Decryption]]
- [[DCSync]]
- [[DCShadow]]
- [[ADCS-ESC1]]
- [[ADCS-ESC2]]
- [[ADCS-ESC3]]
- [[ADCS-ESC4]]
- [[ADCS-ESC8]]
- [[Shadow-Credentials]]
- [[SamAccountName-Spoofing]]
- [[NoPac-CVE-2021-42278]] — Technique _(or CVE)_
- [[Zerologon]] — Technique _(or CVE)_
- [[PrintSpoofer]]
- [[LAPS-Read]]
- [[gMSA-Read]]

## 07-Credential-Access

> All notes here use the **Technique** template. (Tool-style notes for Mimikatz, Hashcat, John live in `03-Tools/`.)

- [[LSASS-Dump]]
- [[SAM-Dump]]
- [[NTDS-Dump]]
- [[LSA-Secrets-Dump]]
- [[Credential-Manager-Dump]]
- [[Browser-Credential-Dump]]
- [[DPAPI-Decryption]]
- [[Hashcat-Cracking]]
- [[John-The-Ripper-Cracking]]
- [[Responder-Poisoning]]
- [[NTLM-Relay]]
- [[Kerberoast-Crack]]
- [[ASREProast-Crack]]

## 08-Lateral-Movement

> All notes here use the **Technique** template.

- [[Pass-The-Hash]]
- [[Pass-The-Ticket]]
- [[Overpass-The-Hash]]
- [[WMI-Execution]]
- [[WinRM-Execution]]
- [[PSExec]]
- [[SMBExec]]
- [[DCOM-Execution]]
- [[SSH-Pivoting]]
- [[RDP-Lateral]]
- [[Port-Forwarding-SSH]]
- [[Chisel-Tunneling]]
- [[Ligolo-Tunneling]]
- [[SOCKS-Proxy-Setup]]
- [[Proxychains-Configuration]]

## 09-Persistence

> All notes here use the **Technique** template.

- [[Scheduled-Task-Persistence]]
- [[Service-Persistence]]
- [[Registry-Run-Keys]]
- [[Startup-Folder-Persistence]]
- [[WMI-Event-Subscription]]
- [[Golden-Ticket]]
- [[Silver-Ticket]]
- [[Diamond-Ticket]]
- [[DSRM-Persistence]]
- [[AdminSDHolder-Abuse]]
- [[SID-History-Injection]]
- [[Skeleton-Key]]

## 10-Defense-Evasion

> All notes here use the **Technique** template.

- [[AMSI-Bypass]]
- [[AppLocker-Bypass]]
- [[ETW-Patching]]
- [[PowerShell-Logging-Bypass]]
- [[Process-Injection]]
- [[Process-Hollowing]]
- [[Unhooking-EDR]]
- [[Direct-Syscalls]]
- [[Indirect-Syscalls]]
- [[String-Obfuscation]]
- [[Payload-Encryption]]

## 11-Command-and-Control

> All notes here use the **Technique** template.

- [[Sliver-Operator-Setup]]
- [[Sliver-Implant-Generation]]
- [[Cobalt-Strike-Listener]]
- [[Cobalt-Strike-Malleable-Profile]]
- [[Mythic-Setup]]
- [[Havoc-Setup]]
- [[Domain-Fronting]]
- [[Redirector-Setup]]

## 12-Collection-Exfiltration

> All notes here use the **Technique** template.

- [[Sensitive-File-Discovery]]
- [[Email-Collection]]
- [[Database-Dump]]
- [[DNS-Exfiltration]]
- [[HTTP-Exfiltration]]
- [[ICMP-Exfiltration]]
- [[Cloud-Storage-Exfil]]

## 13-Reporting

> Mostly **Cheatsheet** template (these are reference/template docs, not techniques).

- [[Report-Structure]] — Cheatsheet
- [[Executive-Summary-Template]] — Cheatsheet
- [[Finding-Writeup-Template]] — Cheatsheet
- [[Screenshot-Conventions]] — Cheatsheet
- [[Risk-Rating]] — Cheatsheet
- [[Remediation-Guidance]] — Cheatsheet

---

# 02-Web-App-Testing

> All notes here use the **Technique** template, with one exception noted below.

## Methodology

- [[Web-App-Testing-Methodology]] — MOC _(this one's a navigation page, not a technique)_
- [[Burp-Setup-And-Workflow]]
- [[Web-Content-Discovery]]
- [[Parameter-Discovery]]
- [[JavaScript-Recon]]

## Injection

- [[SQLi-Authentication-Bypass]]
- [[SQLi-Union-Based]]
- [[SQLi-Boolean-Blind]]
- [[SQLi-Time-Based]]
- [[SQLi-Out-Of-Band]]
- [[Command-Injection]]
- [[SSTI-Server-Side-Template-Injection]]
- [[LDAP-Injection]]
- [[NoSQL-Injection]]
- [[XPath-Injection]]
- [[CRLF-Injection]]

## XSS

- [[Reflected-XSS]]
- [[Stored-XSS]]
- [[DOM-XSS]]
- [[XSS-Filter-Evasion]]
- [[XSS-To-Account-Takeover]]

## CSRF / SOP / CORS

- [[CSRF-Token-Bypass]]
- [[SameSite-Cookie-Bypass]]
- [[CORS-Misconfiguration]]

## AuthN / AuthZ

- [[Broken-Authentication]]
- [[JWT-Attacks]]
- [[OAuth-Attacks]]
- [[SAML-Attacks]]
- [[Session-Fixation]]
- [[Session-Hijacking]]
- [[Privilege-Escalation-Web]]

## IDOR

- [[IDOR-Testing]]
- [[Mass-Assignment]]

## SSRF

- [[SSRF-Basic]]
- [[SSRF-Filter-Bypass]]
- [[SSRF-Cloud-Metadata]]
- [[Blind-SSRF]]

## XXE

- [[XXE-Basic]]
- [[Blind-XXE]]
- [[XXE-File-Read]]
- [[XXE-To-RCE]]

## Deserialization

- [[Java-Deserialization]]
- [[PHP-Deserialization]]
- [[Python-Pickle-Deserialization]]
- [[NET-Deserialization]]
- [[YAML-Deserialization]]

## File Upload

- [[Bypass-Extension-Filter]]
- [[Magic-Bytes-Bypass]]
- [[Content-Type-Bypass]]
- [[Path-Traversal-In-Upload]]
- [[Race-Condition-Upload]]

## Path Traversal

- [[Path-Traversal-Basic]]
- [[Path-Traversal-Encoding-Bypass]]
- [[LFI-To-RCE]]
- [[Log-Poisoning]]

## API Testing

- [[REST-API-Testing]]
- [[GraphQL-Testing]]
- [[SOAP-Testing]]
- [[API-Authentication-Testing]]

## Misc Web

- [[Race-Condition-Testing]]
- [[Web-Cache-Poisoning]]
- [[Request-Smuggling]]
- [[Prototype-Pollution]]
- [[Subdomain-Takeover]]

---

# 03-Tools

> All notes here use the **Tool** template.

## Recon / Enumeration

- [[03-Tools/Recon & Enumeration/Nmap]]
- [[Masscan]]
- [[Rustscan]]
- [[Amass]]
- [[Subfinder]]
- [[theHarvester]]
- [[Recon-ng]]
- [[Gobuster]]
- [[Ffuf]]
- [[Feroxbuster]]
- [[Wfuzz]]
- [[Dirsearch]]
- [[Whatweb]]
- [[Wappalyzer]]

## AD / Windows

- [[BloodHound]]
- [[SharpHound]]
- [[Bloodyad]]
- [[Impacket]]
- [[NetExec]]
- [[Rubeus]]
- [[Mimikatz]]
- [[Kerbrute]]
- [[Evil-WinRM]]
- [[Certipy]]
- [[Adalanche]]
- [[PowerView]]
- [[PowerSploit]]

## Web

- [[Burp-Suite]]
- [[OWASP-ZAP]]
- [[Sqlmap]]
- [[Nuclei]]
- [[Nikto]]

## Credentials / Cracking

- [[Hashcat]]
- [[John-The-Ripper]]
- [[Hydra]]
- [[Medusa]]
- [[Patator]]
- [[Hack the Box/Hack the Box Labs/Starting Point/Starting Point Tier 1/Responder]]
- [[Inveigh]]

## Pivoting

- [[Chisel]]
- [[Ligolo-Ng]]
- [[Sshuttle]]
- [[Proxychains]]

## C2

- [[Sliver]]
- [[Metasploit]]
- [[Empire]]
- [[Havoc]]

## PrivEsc Helpers

- [[Linpeas]]
- [[Winpeas]]
- [[PrivescCheck]]
- [[Linux-Smart-Enumeration]]
- [[PowerUp]]

## Misc

- [[Searchsploit]]
- [[Wireshark]]
- [[Tcpdump]]
- [[Volatility]]
- [[Hashid]]
- [[Cyberchef]]

---

# 04-Payloads

> All notes here use the **Payload** template, with TTY-related exceptions noted.

## Reverse Shells

- [[Reverse-Shell-Bash]]
- [[Reverse-Shell-Python]]
- [[Reverse-Shell-Python3]]
- [[Reverse-Shell-PowerShell]]
- [[Reverse-Shell-PHP]]
- [[Reverse-Shell-Perl]]
- [[Reverse-Shell-Ruby]]
- [[Reverse-Shell-Java]]
- [[Reverse-Shell-MSFVenom]]
- [[Reverse-Shell-NC]]

## Bind Shells

- [[Bind-Shell-Bash]]
- [[Bind-Shell-NC]]

## Web Shells

- [[Web-Shell-PHP]]
- [[Web-Shell-ASPX]]
- [[Web-Shell-JSP]]
- [[Web-Shell-Tomcat-WAR]]

## Encoded / Obfuscated

- [[Base64-Encoded-Payloads]]
- [[UTF-16LE-Encoded-Payloads]]
- [[PowerShell-EncodedCommand]]
- [[URL-Encoded-Payloads]]

## TTY Upgrades

- [[Spawn-TTY-Linux]] — Technique _(this is a process, not a static payload)_
- [[Stabilize-Reverse-Shell]] — Technique

---

# 05-CVEs

> All notes here use the **CVE** template. Don't pre-create — only add when you've actually used the exploit.

_(Examples — fill in as encountered)_

- [[CVE-2017-0144-EternalBlue]]
- [[CVE-2019-0708-BlueKeep]]
- [[CVE-2020-1472-Zerologon]]
- [[CVE-2021-42278-NoPac]]
- [[CVE-2021-44228-Log4Shell]]
- [[CVE-2014-6271-Shellshock]]
- [[CVE-2022-26134-Confluence-OGNL]]
- [[CVE-2023-23397-Outlook-NTLM]]

---

# 06-Boxes-and-Labs

> All notes here use the **Box** template. Created on demand — one per box you actually do.

_(No starter list — this folder grows organically as you do labs.)_

---

# 07-Certs

> All notes here use the **Cert-Roadmap** template.

- [[OSCP-Roadmap]]
- [[PNPT-Roadmap]]
- [[CRTO-Roadmap]]
- [[CRTP-Roadmap]]
- [[OSEP-Roadmap]]
- [[OSWE-Roadmap]]
- [[CPTS-Roadmap]]

---

# 08-MOCs

> All notes here use the **MOC** template.

- [[Active-Directory-MOC]]
- [[Windows-Privilege-Escalation-MOC]]
- [[Linux-Privilege-Escalation-MOC]]
- [[Web-App-Testing-MOC]]
- [[Initial-Access-MOC]]
- [[Post-Exploitation-MOC]]
- [[Pivoting-MOC]]
- [[Credential-Access-MOC]]
- [[Reconnaissance-MOC]]
- [[Enumeration-MOC]]
- [[Kill-Chain-MOC]]
- [[OPSEC-MOC]]

---

# 09-Cheatsheets

> All notes here use the **Cheatsheet** template.

- [[Common-Ports-and-Services]]
- [[Default-Credentials]]
- [[Reverse-Shell-Cheatsheet]]
- [[Linux-Commands-Cheatsheet]]
- [[Windows-Commands-Cheatsheet]]
- [[PowerShell-Cheatsheet]]
- [[Active-Directory-Commands-Cheatsheet]]
- [[Impacket-Cheatsheet]]
- [[BloodHound-Cypher-Queries]]
- [[Nmap-Quick-Reference]]
- [[Burp-Suite-Hotkeys]]
- [[Hashcat-Modes-Reference]]
- [[Hashcat-Rules-Reference]]
- [[Hash-Identification-Reference]]
- [[File-Transfer-Cheatsheet]]
- [[Pivoting-Cheatsheet]]
- [[TTY-Upgrade-Cheatsheet]]
- [[Buffer-Overflow-Cheatsheet]]
- [[GTFOBins-Quick-Lookup]]
- [[LOLBAS-Quick-Lookup]]

---

## Suggested order to start filling in

1. **Build the AD MOC first** — `[[Active-Directory-MOC]]`. Even empty, it organizes your AD reading.
2. **Stub the cheatsheets you'd want exam-day** — `[[Reverse-Shell-Cheatsheet]]`, `[[File-Transfer-Cheatsheet]]`, `[[TTY-Upgrade-Cheatsheet]]`. High-leverage starting point.
3. **Pick your current cert and stub its roadmap** — e.g. `[[OSCP-Roadmap]]`. Surface gaps to focus practice.
4. **Then practice.** Every box creates 2–4 organic technique notes. Don't seed the rest cold.

## Rules of thumb on template choice

The boundary between **Technique** and **Tool** is the most common confusion. The test:

- _Does this note describe a goal-oriented action you take during an engagement?_ → **Technique**. Example: "SMB-Null-Session-Enumeration" is a thing you do.
- _Does this note describe a piece of software, its flags, and its behavior?_ → **Tool**. Example: "Nmap" is a thing you use across many techniques.

When the same word fits both (e.g. "Mimikatz"), the rule is: the _tool_ gets one note in `03-Tools/`, and each _technique_ that uses it (LSASS dumping, DCSync, ticket extraction) gets its own note in the appropriate phase folder. The technique notes link to the tool note via the `tools:` frontmatter field.

**Cheatsheets vs Techniques:** if the note is mostly tables and lookup data you'd reference under time pressure, it's a Cheatsheet. If it's steps you take with prerequisites and pivots, it's a Technique. The "Default-Credentials" cheatsheet in your vault is purely lookup; the "Default-Credential-Testing" technique is the _process_ of using that lookup.

**CVEs vs Techniques:** a CVE note is about the _vulnerability_ — affected versions, detection, remediation. A technique note is about _what you do_ — exploitation steps, pivots after success. PrintNightmare or Zerologon can be modeled either way; some people prefer one note per CVE, some prefer technique notes that reference CVEs in frontmatter. Pick one convention and stick to it. The vault structure here defaults to technique notes for AD-style attacks (Kerberoasting, ADCS-ESC1) and CVE notes for one-shot patches (EternalBlue, Log4Shell).
