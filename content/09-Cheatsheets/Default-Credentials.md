---
publish: true
created: 2026-05-06
modified: 2026-05-07T16:10:43.862Z
---

# Default Credentials

> Quick reference for default credentials on common services. Always try these first — they're embarrassingly often left in place.

> See [[Default Credential Testing]] for the _technique_ of using these systematically.

## Web applications

| Product | Username | Password |
|---------|----------|----------|
| Tomcat Manager | tomcat | tomcat / s3cret / admin |
| Tomcat Manager | admin | admin / password / "" |
| Jenkins | admin | admin / password |
| Apache Solr | (none) | (none) |
| Splunk | admin | changeme |
| Grafana | admin | admin |
| GitLab (initial, < 8.x) | root | 5iveL!fe |
| Nagios | nagiosadmin | PASSW0RD |
| Cacti | admin | admin |
| phpMyAdmin | root | "" / root |
| Webmin | root | (system root pw) |
| WordPress | admin | admin / password |

## Databases

| Product | Username | Password |
|---------|----------|----------|
| MySQL | root | "" / root |
| PostgreSQL | postgres | postgres / "" |
| MSSQL | sa | (blank) / password / sa |
| MongoDB | (none) | (none — older versions) |
| Redis | (none) | (none — default) |
| Oracle | system | manager |
| Oracle | sys | change\_on\_install |
| Oracle | scott | tiger |
| Elasticsearch | elastic | changeme |
| CouchDB | admin | admin |

## Network devices

| Product | Username | Password |
|---------|----------|----------|
| Cisco | cisco | cisco |
| Cisco (enable) | (none) | cisco |
| MikroTik | admin | (blank) |
| Ubiquiti | ubnt | ubnt |
| pfSense | admin | pfsense |
| HP iLO | Administrator | (sticker) |
| Dell iDRAC | root | calvin |
| Supermicro IPMI | ADMIN | ADMIN |

## IoT / Cameras

| Product | Username | Password |
|---------|----------|----------|
| Hikvision | admin | 12345 |
| Dahua | admin | admin |
| Axis | root | pass |
| Generic IP camera | admin | admin / 1234 / "" |

## SNMP community strings

| String | Notes |
|--------|-------|
| public | Read-only, default |
| private | Read-write, default |
| cisco | Cisco devices |
| manager | Some HP devices |

## Application-specific notes

- **Tomcat creds in `tomcat-users.xml`** — if you can read the file, you have creds.
- **Jenkins script console** at `/script` — RCE if authed.
- **Grafana admin/admin** — even after login, check for SSRF (CVE-2021-43798).
- **Oracle scott:tiger** — legacy training account, still alive in lab environments.

## When defaults fail

- Try **username = password** for the discovered usernames.
- Try **username = service name** (e.g. `tomcat:tomcat`, `jenkins:jenkins`).
- Try `[username]:[username]2024`, `[username]:[username]!`, etc.
- Pivot to [[Password Spraying]] using known company-flavored passwords.
- After harvesting any creds elsewhere, come back here for [[Credential Reuse]].

## References

- DefaultCreds-Cheat-Sheet: https://github.com/ihebski/DefaultCreds-cheat-sheet
- cirt.net default passwords: https://cirt.net/passwords
- SecLists default credentials: https://github.com/danielmiessler/SecLists/tree/master/Passwords/Default-Credentials

## Related notes

- [[Default Credential Testing]]
- [[Password Spraying]]
- [[Credential Reuse]]
