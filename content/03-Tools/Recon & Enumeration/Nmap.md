---
publish: true
created: 2026-05-06
modified: 2026-05-06T17:16:28.553Z
---

# Nmap

> Network exploration and security auditing — host discovery, port scanning, service/version detection, and scriptable enumeration via NSE.

## Installation

```bash
# Debian/Ubuntu/Kali
sudo apt install nmap

# Verify
nmap --version
```

## Core flags

| Flag | Purpose | Example |
|------|---------|---------|
| `-sS` | TCP SYN (stealth) scan — default as root | `nmap -sS <ip>` |
| `-sT` | TCP Connect scan — used when not root | `nmap -sT <ip>` |
| `-sU` | UDP scan | `nmap -sU --top-ports 100 <ip>` |
| `-sn` | Ping/host discovery only, no port scan | `nmap -sn 10.10.10.0/24` |
| `-Pn` | Skip host discovery, treat as up | `nmap -Pn <ip>` |
| `-p-` | All 65535 ports | `nmap -p- <ip>` |
| `-p <range>` | Specific ports | `nmap -p 22,80,443 <ip>` |
| `--top-ports N` | Top N most common ports | `nmap --top-ports 1000 <ip>` |
| `-sV` | Service version detection | `nmap -sV <ip>` |
| `-sC` | Default NSE scripts | `nmap -sC <ip>` |
| `-A` | Aggressive: -sV -sC -O --traceroute | `nmap -A <ip>` |
| `-O` | OS fingerprinting | `nmap -O <ip>` |
| `-oA <basename>` | Output all formats (normal/grepable/XML) | `nmap -oA scans/initial <ip>` |
| `-T0..-T5` | Timing template (paranoid → insane) | `nmap -T4 <ip>` |
| `--min-rate N` | Min packets per second | `nmap --min-rate 5000 <ip>` |
| `--script <s>` | Run specific NSE script(s) | `nmap --script vuln <ip>` |
| `--reason` | Show why each port is open/closed/filtered | `nmap --reason <ip>` |
| `--open` | Only show open ports in output | `nmap -p- --open <ip>` |

## Common invocations

### Host discovery

```bash
nmap -sn -PE -PS80,443 -PA80,443 10.10.10.0/24 -oA scans/hosts
```

### Quick port scan + service detection (all TCP)

```bash
nmap -p- --min-rate 5000 -sCV <ip> -oA scans/tcp-full
```

### Two-stage (faster on slow targets)

```bash
nmap -p- --min-rate 5000 <ip> -oA scans/tcp-all
ports=$(grep ^[0-9] scans/tcp-all.gnmap | grep open | awk -F'/' '{print $1}' | tr '\n' ',')
nmap -sCV -p$ports <ip> -oA scans/tcp-detailed
```

### UDP top 100 (full UDP is impractically slow)

```bash
nmap -sU --top-ports 100 <ip> -oA scans/udp
```

### Vulnerability scripts

```bash
nmap --script "vuln and not (broadcast or dos)" -p<ports> <ip>
```

### SMB-specific

```bash
nmap --script "smb-vuln-* and safe" -p139,445 <ip>
nmap --script smb-os-discovery -p445 <ip>
```

### HTTP enumeration

```bash
nmap --script "http-enum,http-title,http-headers,http-methods" -p80,443,8080 <ip>
```

## Tips & gotchas

- **`-A` is loud and slow.** Don't reach for it reflexively. Use `-sCV` for most cases.
- **Default SYN scan needs root.** Without root, nmap silently falls back to `-sT`, which is louder.
- **`-Pn` matters more than people think.** Many lab targets and some real ones drop ICMP. Without `-Pn`, nmap reports them down and skips them.
- **`-oA` saves output in three formats.** The grepable one (`.gnmap`) is invaluable for quick port extraction with awk.
- **NSE scripts have categories**: `safe`, `intrusive`, `vuln`, `auth`, `default`, `discovery`. Combine safely with `--script "default and safe"`.
- **`--reason`** shows why nmap classified each port — useful when "filtered" vs "closed" is confusing you.
- **`--open`** filters output to only open ports. Cleaner reading.
- **Resume** with `--resume scans/tcp-all.normal` if interrupted.

## OPSEC notes

- Default SYN scan is half-open and won't appear in most application logs, but is highly visible to network IDS.
- `-T4`/`-T5` are loud; use `-T2` or `-T1` for slow-and-quiet.
- `--scan-delay` adds delay between probes; `--max-rate` caps it.
- `-D <decoy1,decoy2,ME>` adds spoofed source IPs to obscure your scan in logs.
- `--data-length N` pads packets to evade simple signatures.

## Alternatives

- **rustscan** — much faster initial port discovery, hands off to nmap for service detection. Reach for it when nmap's `-p- --min-rate 5000` is still too slow.
- **masscan** — internet-scale scanning. For wide ranges, not single hosts.
- **naabu** — Go-based, fast.

## Techniques that use this tool

## References

- nmap reference guide: https://nmap.org/book/
- NSE script database: https://nmap.org/nsedoc/
- HackTricks pentesting network: https://book.hacktricks.xyz/
