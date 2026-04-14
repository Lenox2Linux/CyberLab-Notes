# 🔌 Ports & Protocols

**Domain:** A+ Core 1 2.0 | Network+ 1.0
**Professor Messer:** A+ Section 2.1 | Network+ Section 1.4
**Tags:** #ports #protocols #comptia #aplus #networkplus

---

## 📖 Definition
Ports are logical communication endpoints. Protocols define rules for communication.

---

## 🔑 Must-Know Ports

| Port | Protocol | Description | TCP/UDP |
|---|---|---|---|
| 20 | FTP | File Transfer data | TCP |
| 21 | FTP | File Transfer control | TCP |
| 22 | SSH | Secure Shell | TCP |
| 23 | Telnet | Unsecure remote access | TCP |
| 25 | SMTP | Send email | TCP |
| 53 | DNS | Domain Name System | TCP/UDP |
| 67/68 | DHCP | IP address assignment | UDP |
| 80 | HTTP | Web traffic | TCP |
| 110 | POP3 | Receive email | TCP |
| 143 | IMAP | Receive email synced | TCP |
| 161/162 | SNMP | Network monitoring | UDP |
| 389 | LDAP | Directory services | TCP |
| 443 | HTTPS | Secure web traffic | TCP |
| 445 | SMB | File sharing Windows | TCP |
| 514 | Syslog | Log forwarding | UDP |
| 636 | LDAPS | Secure LDAP | TCP |
| 3389 | RDP | Remote Desktop | TCP |

---

## 🔑 Port Ranges
- 0-1023 = Well-known ports
- 1024-49151 = Registered ports
- 49152-65535 = Dynamic/ephemeral ports

---

## ⚠️ Exam Gotchas
- DNS uses both TCP and UDP
- DHCP uses UDP
- SMB 445 replaced NetBIOS 137-139
- IMAP keeps mail on server, POP3 downloads and deletes

---

## 🧠 INTELUX Lab Connection
- Port 514 UDP = Suricata rsyslog pipeline
- Port 1514/1515 = Wazuh agent communication
- Port 443 = Caddy HTTPS reverse proxy
- Port 9200 = Wazuh indexer
- Port 3389 = RDP used in Kill Chain A

---

## 🔗 Related Topics
- [[OSI-Model]]
- [[TCP-IP-Suite]]
- [[Network-Security-Concepts]]

---

## 📅 Last Reviewed
