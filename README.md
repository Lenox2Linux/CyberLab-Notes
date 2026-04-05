# INTELUX Systems, Inc.
### Enterprise Security Operations & Infrastructure
`intelux.local` · New York City, NY · Est. 2026

---

> A portfolio-quality enterprise homelab built from scratch — VLAN-segmented network, live SIEM, GRC program, and active red team operations. Every failure documented. Every lesson earned.

---

## What This Is

INTELUX is a simulated enterprise security environment designed to mirror real production infrastructure. Not a tutorial lab. Not a sandbox. A functioning security operations environment with segmented VLANs, centralized monitoring, formal documentation, and ongoing attack/defense exercises.

Built and operated by **Raynard A. Porter** — A.A.S. Cybersecurity candidate at Westchester Community College, targeting Security+ (May 2026) and SOC/GRC analyst roles.

---

## Network Architecture

| VLAN | Name | Subnet | Purpose |
|------|------|--------|---------|
| 10 | MGMT | 10.100.10.0/24 | Switch management, ADM-01, HV-01 |
| 20 | SERVICES | 10.100.20.0/24 | Docker stack, Wazuh, DC-01, WEB-01 |
| 30 | CLIENTS | 10.100.30.0/24 | Victim workstations, blue/red team exercises |
| 40 | PORTAL | 10.100.40.0/24 | Kiosk — Kill Chain B entry point |
| 50 | STAGING | 10.100.50.0/24 | Red team, isolated from all other VLANs |
| 60 | DMZ | 10.100.60.0/24 | Internet-facing services — WEB-01 (planned) |

Routing and inter-VLAN firewall policy enforced by **pfSense CE 2.7.2** on INTELUX-HV-01.

---

## Physical Infrastructure

| Device | Role | Hardware | Platform |
|--------|------|----------|----------|
| INTELUX-HV-01 | Primary Hypervisor | Lenovo M920 Tower · i5-8500 · 16GB · 476GB NVMe | Proxmox VE 8 |
| INTELUX-CL-01 | Victim/Honeypot Host | Lenovo M910 Tower · i5-7500 · 16GB | Proxmox VE 8 |
| INTELUX-SRV-01 | Services Server | Apple Mac Mini 2014 · i5-4278U · 8GB | Ubuntu 24.04 / Docker |
| INTELUX-RED-01 | Red Team Host | Apple MacBook Pro 2012 · 8GB | Parrot OS (bare metal) |
| INTELUX-ADM-01 | Admin Workstation | Lenovo ThinkPad T14 · Ryzen 7 PRO 5850U · 16GB | Windows 11 Enterprise |
| INTELUX-SW-01 | Managed Switch | Netgear GS308E | GS308E Firmware |

---

## Security Stack

| Tool | Category | Purpose |
|------|----------|---------|
| Wazuh v4.14.3 | SIEM / EDR | Endpoint detection, FIM, log aggregation, alerting |
| pfSense 2.7.2 | Firewall / Router | Perimeter firewall, VLAN routing, outbound NAT |
| Suricata | IDS/IPS | Network intrusion detection on WAN (EVE JSON → Wazuh) |
| Grafana + Prometheus | Monitoring | Infrastructure dashboards, node metrics |
| Pi-hole v6.4 | DNS | Internal DNS resolver, DHCP |
| Vaultwarden | Password Mgmt | Self-hosted credential vault |
| Caddy | Reverse Proxy | HTTPS termination, `*.intelux.local` subdomains |
| Tailscale | Remote Access | Subnet router advertising 10.100.0.0/16 |
| PhishTix | Portfolio Project | Custom Flask phishing analysis training tool |
| Parrot OS / Kali | Red Team | Penetration testing, OSINT, attack simulation |

---

## Repository Structure

```
CyberLab-Notes/
├── 01-Home Cyber Lab Architecture/   # VLAN design, hardware inventory, topology
├── 02-Isolated Zone/                 # STAGING (VLAN 50) — red team infrastructure
├── 03-Trusted Zone/                  # MGMT/SERVICES/CLIENTS — production zones
├── 04-Equipment/                     # Hardware specs, SMART data, asset registry
├── 05-OS/                            # OS configs, hardening notes
├── 06-VM/                            # VM registry, Proxmox config
├── 07-Diagrams/                      # Network topology diagrams
├── 08-Screenshots/                   # Evidence artifacts
├── 09-Incidents & Lessons/           # Incident reports, post-mortems, lessons
├── 10-Professional Development/      # Cert roadmap, study notes, career target
├── 00-Templates/                     # Incident report, change log, runbook templates
└── 99-Retired/                       # Archived configs and deprecated docs
```

---

## GRC Program

ISO 27001:2022 compliance matrix covering 28 Annex A controls across 4 domains. As of April 2026:

| Status | Controls | % |
|--------|----------|---|
| Implemented | 13 | ~46% |
| Partial | 10 | ~36% |
| Planned | 4 | ~14% |
| N/A | 1 | ~4% |

Key completed controls: A.5.26 (incident response), A.8.7 (malware protection), A.8.15 (logging), A.8.16 (monitoring), A.8.22 (network segregation).

Active risk register and change control documentation maintained per sprint.

---

## Operations Log (Current Sprint — April 2026)

**Completed:**
- Suricata WAN deployment with EVE JSON → Wazuh pipeline
- Vaultwarden MFA enforced
- Caddy reverse proxy fully configured (`*.intelux.local`, `tls_trust_pool` Wazuh CA trust)
- GRC change control documents L-1, L-2, L-6
- DC-01 deployed (Windows Server 2022, 10.100.20.102, VLAN 20)

**In Progress:**
- East-west Docker isolation on SRV-01
- VLAN 60 DMZ — pfSense + WEB-01 at 10.100.60.10
- Kill Chain A — authorized pentest, RED-01 → WKS-03 (VLAN 50 → VLAN 30)

---

## Certification Roadmap

```
[NOW]  CompTIA Security+  →  May 2026
       GCIH               →  Late 2026
       OSCP               →  2027
[TARGET]  EY Cyber Threat Detection — Active Defense Analyst
```

---

## Key Documents

| Document | Category | Status |
|----------|----------|--------|
| INTELUX_Master_Asset_Inventory v1.11 | Overview | Complete |
| INTELUX_pfSense_VLAN_Runbook v1.1 | Network | Complete |
| INC-001_WindowsUpdate_FalsePositive | SOC / IR | Complete |
| INTELUX_ISO27001_Compliance_Matrix v1.0 | GRC | Complete |
| INTELUX_Company_Profile v1.1 | Overview | Complete |
| INTELUX_Risk_Register | GRC | In Progress |
| INTELUX_RedTeam_Rules_of_Engagement | Red Team | Planned |
| INTELUX_Network_Topology_Diagram | Network | Planned |

---

## The Build Journal

The full technical narrative — every OPNsense failure, every switch config bug, every hard-won lesson from February to April 2026 — is documented in `09-Incidents & Lessons/`. If you want to understand how this environment was actually built, that's where to start.

---

*INTELUX-CORP-001 · Classification: Public Portfolio · Owner: Raynard A. Porter (Lenox2Linux) · Last Updated: April 2026*
