---
publish: true
created: 2026-05-06
modified: 2026-05-08T16:02:32.144Z
---

# TCP Port Scan

> Identify TCP ports that are open or filtered on a confirmed-live host.

## Trigger

- Host is confirmed reachable (see [[Host Discovery]]).
- You don't yet know which services are listening.
- Always the second action against a target after host discovery.

## Prerequisites

- Live target IP.
- Network connectivity (ideally not behind asymmetric NAT).
- Tools: [[03-Tools/Recon & Enumeration/Nmap]] (primary), [[Masscan]] / [[Rustscan]] for fast wide scans.

## Procedure

### Two-stage scan (the standard approach)

```bash
# Stage 1: full TCP port range, fast
nmap -p- --min-rate 5000 -T4 <ip> -oA scans/tcp-all

# Extract open ports
ports=$(grep ^[0-9] scans/tcp-all.gnmap | grep open | awk -F'/' '{print $1}' | tr '\n' ',')

# Stage 2: deep scan of just those ports
nmap -sCV -p$ports <ip> -oA scans/tcp-detailed
```

### One-liner version

```bash
nmap -p- --min-rate 5000 -T4 -sCV <ip> -oA scans/tcp-full
```

(Slower because version detection runs against all 65k ports.)

### Fast initial sweep with rustscan

```bash
rustscan -a <ip> --ulimit 5000 -- -sCV -oA scans/tcp-rustscan
```

### Expected output

```
PORT     STATE SERVICE     VERSION
22/tcp   open  ssh         OpenSSH 7.6p1 Ubuntu 4ubuntu0.7
80/tcp   open  http        Apache httpd 2.4.29
445/tcp  open  netbios-ssn Samba smbd 4.7.6-Ubuntu
```

## Pivot

For each open port, head to the corresponding service enumeration note. See [[Common Ports and Services]] for the full lookup. Most common pivots:

- 21 → [[FTP Enumeration]]
- 22 → [[SSH Enumeration]]
- 80 / 443 / 8080 → [[HTTP Enumeration]]
- 139 / 445 → [[SMB Enumeration]]
- 389 / 636 → [[LDAP Enumeration]]
- 1433 → [[MSSQL Enumeration]]
- 3306 → [[MySQL Enumeration]]
- 3389 → [[RDP Enumeration]]
- 5985 / 5986 → [[WinRM-Enumeration]]

Don't forget to also run [[UDP Port Scan]] — many engagements miss SNMP, TFTP, IKE, NFS because UDP wasn't scanned.

## OPSEC / Detection

- **Noise profile:** loud. SYN scan against all 65k ports is one of the most distinctive patterns in IDS signatures.
- `-T4` and `--min-rate 5000` will trigger most modern IDS.
- For evasion: `-T2` or lower, `--scan-delay`, fragment with `-f`, decoy IPs with `-D`.
- SYN scan (`-sS`, default as root) is half-open — won't show in app logs but absolutely shows in network logs.
- TCP Connect scan (`-sT`) completes the handshake — application logs will see it.

## Common pitfalls

- Stopping at the top 1000 ports. Always run `-p-` somewhere in your methodology.
- Trusting `-sV` to identify everything — it misses non-standard services on weird ports. Banner-grab manually with `nc` to confirm.
- Forgetting to scan UDP. Real engagements lose hours because of this.
- Not saving output (`-oA`) — when you need to check "what was on port 8443 again" two days later, you'll regret it.
- Running scripts (`-sC`) in stage 1 against all 65k ports — wastes hours.

## Variants

- **TCP Connect scan** (no root): `nmap -sT`
- **Stealthier**: `nmap -sS -T2 --scan-delay 1s`
- **Top 1000 only** (when time-constrained): `nmap -sCV --top-ports 1000`
- **Mass scanning at scale**: `masscan -p1-65535 --rate 10000 <range>`

## References

- nmap port scanning techniques: https://nmap.org/book/man-port-scanning-techniques.html
- HackTricks port scanning: https://book.hacktricks.xyz/

## Related notes

- [[03-Tools/Recon & Enumeration/Nmap]]
- [[Host Discovery]]
- [[UDP Port Scan]]
- [[Service Version Detection]]
- [[Common Ports and Services]]
