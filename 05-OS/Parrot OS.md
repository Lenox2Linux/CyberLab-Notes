# 🦜 Parrot OS — INTELUX-RED-01

**Updated:** 2026-04-05
**Status:** Active — primary red team OS

---

## Deployment

| Field        | Value                             |
| ------------ | --------------------------------- |
| Host         | INTELUX-RED-01 (MacBook Pro 2012) |
| Install Type | Bare-metal (full disk wipe)       |
| Edition      | Parrot OS Security Edition        |
| VLAN         | 50 — STAGING                      |
| Wazuh Agent  | None (intentional — OPSEC)        |

---

## Why Parrot OS Over Kali

| Factor | Notes |
|---|---|
| Resource efficiency | Better performance on aging MacBook Pro hardware |
| Stability | More stable on older Intel hardware than recent Kali builds |
| Toolset | Full security toolset included — nmap, Metasploit, Wireshark, Burp Suite |
| Bare-metal | Full hardware dedicated — no VM overhead |

---

## Installed / Configured

- Parrot OS Security Edition (full toolset)
- macfanctld — MacBook fan control under Linux
- APT repositories accessible (verified post 2026-04-02 firewall fix)
- Standard Parrot security toolset active

---

## Active Operations

- **Kill Chain A:** Authorized pentest against WKS-03 (10.100.30.x, VLAN 30)
  - Black box methodology
  - nmap SYN scan in progress — `-Pn` flag required
  - Launched from RED-01 (10.100.50.x)

---

## Build History

See [[RED-01-Build-History]] for the full evolution from macOS Monterey → Kali VM → Parrot OS bare-metal.

---

## Related Notes
- [[INTELUX-RED-01 — Apple MacBook Pro (2012)]]
- [[RED-01-Build-History]]
- [[Isolated-Zone]]
- [[OS-Registry]]
