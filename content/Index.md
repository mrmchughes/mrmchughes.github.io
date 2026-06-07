# Hack the rest of the f\*cking owl

This is an evolving document where I store my offensive security notes. The title is a reference to the "draw the rest of the owl" meme - a tutorial that tells you to start with two simple circles, then jumps straight to a fully detailed owl with nothing in between. I've noticed that certain hacking tutorials will explain how to do something, but not the full reasoning behind why it works. The goal is to make these notes something that someone who is just learning can follow, while also being useful to those who are more advanced.

## The methodology

The full attack lifecycle is mapped in the [[Kill Chain MOC]] - start there for the phase-by-phase walkthrough. The major areas:

- [[Reconnaissance MOC|Reconnaissance]] - gathering information from the outside in
- [[Enumeration MOC|Enumeration]] - turning access into a detailed map of the target
- [[Initial Access MOC|Initial Access]] - getting that first foothold
- [[Credential Access MOC|Credential Access]] - dumping and cracking credentials once you're inside
- Privilege Escalation - [[Linux Privilege Escalation MOC|Linux]], [[Windows Privilege Escalation MOC|Windows]], and [[Active Directory MOC|Active Directory]]
- [[Pivoting MOC|Lateral Movement & Pivoting]] - moving between hosts once you're in
- [[Post Exploitation MOC|Post-Exploitation]] - persistence, evasion, collection, and exfil

## Web & operations

- [[Web App Testing MOC|Web Application Testing]] - the full web track, from recon to exploitation
- [[OPSEC MOC|OPSEC]] - staying quiet and clean throughout

Tools, payloads, and cheatsheets live in the sidebar on the left.

## Scope & ethics

All content here comes from legal, authorized practice environments. No active Hack The Box machine writeups, no certification exam content, and no coursework. This is educational, defensive-minded work: understanding how offense works in order to build and defend better.

## About

Michael Hughes - Graduate cybersecurity student focused on offensive security, working toward red-team roles. Open to opportunities in the Boston area.
