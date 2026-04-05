# 💿 Operating Systems — INTELUX Asset OS Registry

**Updated:** 2026-04-05

---

## Active OS Deployments

| Host | OS | Version | Role |
|---|---|---|---|
| HV-01 | Proxmox VE | Latest | Hypervisor |
| CL-01 | Proxmox VE | Latest | Hypervisor |
| SRV-01 | Ubuntu Server | 22.04 LTS (Jammy Jellyfish) | Docker services host |
| ADM-01 | Windows 11 Pro | Current | Admin workstation |
| RED-01 | Parrot OS | Current | Red team / penetration testing |
| pfSense | pfSense CE | Current | Firewall / router |

---

## VM Operating Systems

| VM | Host Hypervisor | OS | Notes |
|---|---|---|---|
| DC-01 (planned) | HV-01 | Windows Server 2022 | Domain Controller |
| WEB-01 | HV-01 | TBD | Internal/DMZ web server |
| WKS-01 (VM101) | HV-01 | TBD | Client workstation — ossec.conf update pending |
| WKS-03 | CL-01 | TBD | Kill Chain A target |
| WKS-04 | CL-01 | TBD | Out of scope |
| INTELUX-KSK-01 | TBD | TBD | PORTAL kiosk — Kill Chain B |

---

## Key OS Notes

### Ubuntu 22.04 LTS — SRV-01
- Docker + Docker Compose for all services
- Tailscale subnet router (`accept-dns=false` to prevent resolv.conf overwrite)
- Wazuh timezone: America/New_York
- Pi-hole DNS records for `*.intelux.local` pointing to 10.100.20.101

### Parrot OS — RED-01
- macfanctld for fan control (MacBook hardware)
- APT repos accessible post-2026-04-02 firewall fix
- Intel HD 3000 (SNB GT2) — limited GPU

### Windows 11 Pro — ADM-01
- Wazuh agent T2/008 active
- FIM monitoring enabled
- Known false positive patterns documented (Windows Update = Event 4672/4738, FIM registry deletions under `HKLM\CurrentControlSet\Services\`)

---

## Previous OS Deployments (Phase 0 Reference)

| Old | New | Notes |
|---|---|---|
| Kali Linux (VirtualBox) | Parrot OS (bare metal) | Red team machine |
| Linux Mint (VirtualBox) | Retired | No longer in use |
| Mac OS 12 Monterey | Ubuntu 22.04 LTS | SRV-01 repurposed |
| Windows 10 Pro | Windows 11 Pro | ADM-01 upgrade |
| Ubuntu Jammy Jellyfish (VirtualBox) | Native Ubuntu on SRV-01 | Bare metal, no VirtualBox |
| Oracle VirtualBox | Proxmox VE | Full hypervisor replacement |

---

## Related Notes
- [[Equipment-Inventory]]
- [[VM-Registry]]
- [[INTELUX-SRV-01 — Apple Mac Mini (Late 2014)]]