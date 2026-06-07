---
publish: true
created: 2026-05-06
modified: 2026-05-07T16:04:50.008Z
---

# Common Ports and Services

> Quick lookup: see a port → know what to check first → link to the technique. Living document — add ports as you encounter them.

## Top encounters (memorize these)

| Port | Proto | Service | First check |
|------|-------|---------|-------------|
| 21 | TCP | FTP | Anonymous login → [[FTP Enumeration]] |
| 22 | TCP | SSH | Version, banner, key auth → [[SSH Enumeration]] |
| 23 | TCP | Telnet | Banner, default creds |
| 25 | TCP | SMTP | VRFY/EXPN user enum → [[SMTP Enumeration]] |
| 53 | TCP/UDP | DNS | Zone transfer, subdomain enum → [[DNS Enumeration]] |
| 80 | TCP | HTTP | Headers, robots.txt, gobuster → [[HTTP Enumeration]] |
| 88 | TCP | Kerberos | AS-REP roast, user enum → [[Kerberos Enumeration]] |
| 110 | TCP | POP3 | Banner, default creds |
| 111 | TCP/UDP | RPCbind | rpcinfo → maps to NFS, NIS |
| 135 | TCP | MSRPC | rpcdump, endpoint enum |
| 139 | TCP | NetBIOS | enum4linux → [[SMB Enumeration]] |
| 143 | TCP | IMAP | Banner, default creds |
| 161 | UDP | SNMP | Community strings → [[SNMP Enumeration]] |
| 389 | TCP | LDAP | Anonymous bind → [[LDAP Enumeration]] |
| 443 | TCP | HTTPS | Cert info, vhost enum → [[HTTP Enumeration]] |
| 445 | TCP | SMB | Null session, shares → [[SMB Enumeration]] |
| 464 | TCP | Kerberos kpasswd | AD indicator |
| 587 | TCP | SMTP submission | Same as 25 |
| 636 | TCP | LDAPS | Encrypted LDAP → [[LDAP Enumeration]] |
| 873 | TCP | rsync | List modules, anonymous read |
| 1433 | TCP | MSSQL | xp\_cmdshell, login → [[MSSQL Enumeration]] |
| 1521 | TCP | Oracle DB | TNS poisoning, default SIDs |
| 2049 | TCP | NFS | showmount, mount → [[NFS Enumeration]] |
| 2375 | TCP | Docker API | Unauth = host RCE |
| 3268 | TCP | LDAP Global Catalog | AD forest indicator |
| 3306 | TCP | MySQL | Default creds → [[MySQL Enumeration]] |
| 3389 | TCP | RDP | BlueKeep check, login → [[RDP Enumeration]] |
| 5432 | TCP | PostgreSQL | Default creds → [[PostgreSQL Enumeration]] |
| 5601 | TCP | Kibana | Often unauth |
| 5900 | TCP | VNC | No-auth, weak passwords |
| 5985 | TCP | WinRM (HTTP) | evil-winrm → [[WinRM-Enumeration]] |
| 5986 | TCP | WinRM (HTTPS) | Same as 5985 |
| 6379 | TCP | Redis | Unauth → RCE |
| 6443 | TCP | Kubernetes API | kubeconfig leakage |
| 8080 | TCP | HTTP alt | Tomcat, Jenkins, proxies |
| 8443 | TCP | HTTPS alt | Same as 8080 |
| 8888 | TCP | HTTP alt | Often dev/admin |
| 9090 | TCP | HTTP alt | Cockpit, Prometheus |
| 9200 | TCP | Elasticsearch | Often unauth |
| 11211 | TCP/UDP | Memcached | Unauth read |
| 27017 | TCP | MongoDB | Often unauth |

## AD environment indicators

If you see this combination, it's almost certainly a Domain Controller:

> **53 (DNS) + 88 (Kerberos) + 389 (LDAP) + 445 (SMB) + 464 (kpasswd) + 636 (LDAPS) + 3268 (Global Catalog) + 3269 (GC over SSL)**

Action: jump to [[Active-Directory-MOC]] before per-service enumeration.

## Web indicators

- **80, 443, 8080, 8443, 8000, 8888, 3000, 5000** — multiple web services suggest a target rich in web app vulns.
- Action: → [[HTTP Enumeration]] for each. Don't skip the high ports.

## Database indicators

- **1433, 1521, 3306, 5432, 6379, 9200, 11211, 27017** — credential reuse target. After harvesting creds elsewhere, come back here.

## "Weird port" approach

When you see a non-standard port:

1. `nc -nv <ip> <port>` — grab a banner.
2. `curl -sI http://<ip>:<port>/` — many things speak HTTP on weird ports.
3. `nmap -sV -p <port> <ip>` — version detection.
4. Once you've identified the service, swap to its enumeration note.

## References

- SpeedGuide port database: https://www.speedguide.net/ports.php
- HackTricks pentesting ports: https://book.hacktricks.xyz/
