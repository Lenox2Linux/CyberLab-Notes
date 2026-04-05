# 💻 INTELUX-RED-01 — Apple MacBook Pro (2012)

**Updated:** 2026-04-05 **INTELUX Role:** Primary Red Team Attack Platform **Status:** Active

---

## Acquisition & Evolution

|Phase|Role|OS|
|---|---|---|
|Phase 0|Kali lab workstation (macOS base)|macOS Monterey|
|Phase 0.5|Kali Linux VM added inside macOS|macOS + Kali VM (VirtualBox)|
|Phase 1 (Current)|Bare-metal red team host|Parrot OS (full wipe)|

> Full rebuild documented in [[RED-01-Build-History]]

---

## Hardware Specifications

| Field   | Value                                 |
| ------- | ------------------------------------- |
| Model   | Apple MacBook Pro (Mid 2012)          |
| CPU     | Intel Core i5-3210M @ 2.50GHz (2C/4T) |
| GPU     | Intel HD 3000 (SNB GT2)               |
| RAM     | 16 GB                                 |
| Storage | 500 GB HDD                            |
| OS      | Parrot OS (bare metal)                |
|         |                                       |
| Battery | Degraded — replacement ordered        |

---

## Wazuh Agent

**None — intentional. Documented in asset inventory as N/A (OPSEC).** Red team machines have no monitoring agents by design.

---

## Installed Tools

- Parrot OS (full security edition)
- macfanctld (fan control for MacBook hardware)
- APT repos accessible (post 2026-04-02 firewall fix)
- nmap, Metasploit, standard Parrot OS toolset

---

## Known Issues

|Issue|Status|Notes|
|---|---|---|
|Battery degraded|Replacement ordered|Thermal repaste planned after battery swap|
|Intel HD 3000|Limitation|Old GPU — limited to CPU-based tools|
|Internet access broken post-VLAN migration|Resolved 2026-04-02|Root cause: pfSense rule order (Block Lab_Subnets above egress allows)|

---

## Active Operations

- **Kill Chain A:** nmap SYN scan against WKS-03  — in progress
    - `-Pn` flag required (WKS-03 blocks ping probes)
    - Black box methodology

---

## Proxmox Console Note

⚠️ Not applicable — RED-01 is bare metal, accessed via SSH or direct keyboard.

---

## Related Notes

- [[RED-01-Build-History]]
- [[Isolated-Zone]]
- [[Kill-Chain-A]]
- [[Lab-Architecture-Overview]]