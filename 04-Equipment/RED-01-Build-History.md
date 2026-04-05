# 🔴 RED-01 Build History — MacBook Pro (2012)

**Updated:** 2026-04-05
**Device:** Apple MacBook Pro (Mid 2012)
**Current State:** Parrot OS bare-metal, VLAN 50 STAGING

---

## Build Timeline

### Stage 1 — Phase 0: macOS Monterey Baseline
**Period:** Early 2026

The MacBook Pro (2012) started as a personal machine running macOS Monterey. To begin lab use without disrupting the base OS, the machine was kept on macOS and a controlled attack environment was built inside it.

- Downloaded macOS Monterey installer
- Created bootable USB via Terminal `createinstallmedia`
- Wiped internal drive using Disk Utility
- Clean macOS install from bootable USB
- Post-install validation: `ip a`, hostname, connectivity tests

At this stage the machine served as the physical host for a virtualized Kali environment.

---

### Stage 2 — Kali Linux VM Added
**Period:** Mid Phase 0

With macOS as the base, Kali Linux was deployed as a VirtualBox VM inside macOS. This allowed red team tooling without modifying the host OS.

- VirtualBox installed on macOS
- Kali Linux ISO downloaded and verified
- Kali VM created with dual adapters:
  - NAT (internet/updates)
  - Internal Network (isolated lab segment)
- Static IP assigned on internal network segment
- Tools validated: nmap, Metasploit, standard Kali toolset

This stage is documented in [[Kali Cyber Lab Rebuild]] (archived in `99-Retired`).

**Limitation identified:** VirtualBox VM overhead, macOS resource consumption, and the Double NAT architecture limited the machine's effectiveness as a dedicated attack platform.

---

### Stage 3 — Full Wipe, Parrot OS Bare-Metal
**Period:** Pre-VLAN migration

As the lab evolved toward enterprise-grade architecture, the decision was made to fully dedicate the MacBook Pro to red team operations. macOS was wiped and Parrot OS was installed bare-metal.

**Decision rationale:**
- Eliminate VM overhead — full hardware dedicated to attack tooling
- Parrot OS preferred over Kali for its stability and resource efficiency on older hardware
- Aligns with INTELUX STAGING VLAN (50) architecture
- OPSEC decision: no Wazuh agent on RED-01 (documented in asset inventory)

**Install process:**
- Parrot OS Security Edition ISO flashed to USB via BalenaEtcher
- MacBook booted from USB (hold Option at startup)
- Full disk wipe — macOS completely removed
- Parrot OS installed bare-metal
- macfanctld installed for fan control (MacBook hardware requires manual fan management under Linux)
- Network configured for VLAN 50 STAGING (10.100.50.100)
- APT repos verified accessible

---

### Stage 4 — VLAN Migration & Current State
**Period:** March 30, 2026

As part of the full INTELUX VLAN migration (192.168.1.x → 10.100.x.x), RED-01 was migrated to VLAN 50 STAGING.

- Connected to SW-01 P5
- Internet access initially broken post-migration — root cause: pfSense rule order (Block Lab_Subnets above egress allows). Fixed 2026-04-02.
- Kill Chain A exercise begun: authorized pentest against WKS-03

**Current hardware status:**
- Battery degraded — replacement ordered
- Thermal repaste planned post battery replacement

---

## Summary

| Stage | OS | Architecture | Period |
|---|---|---|---|
| 1 | macOS Monterey | Standalone personal machine | Early 2026 |
| 2 | macOS + Kali VM | VirtualBox, Double NAT lab | Mid Phase 0 |
| 3 | Parrot OS bare-metal | Dedicated red team host | Pre-VLAN migration |
| 4 | Parrot OS bare-metal | VLAN 50 STAGING, INTELUX | March 2026–present |

---

## Related Notes
- [[INTELUX-RED-01 — Apple MacBook Pro (2012)]]
- [[Isolated-Zone]]
- [[(Phase 0) Multi-Tiered Defensive Architecture & Cybersecurity Lab Isolation]]
- [[Kali Cyber Lab Rebuild]]
