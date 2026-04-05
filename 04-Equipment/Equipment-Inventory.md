# 🖥️ Equipment Inventory

**Updated:** 2026-04-05
**Standard Username:** aredeebee
**Internal Domain:** intelux.local

---

## Active Hardware

### HV-01 — Primary Hypervisor
| Field | Value |
|---|---|
| Model | Lenovo ThinkCentre M920t |
| Role | Proxmox VE — primary hypervisor |
| IP | 10.100.10.101 (VLAN 10 MGMT) |
| Wazuh Agent | 290 / ID 010 |
| Notes | Hosts most lab VMs |

### CL-01 — Client Hypervisor
| Field | Value |
|---|---|
| Model | Lenovo ThinkCentre M910t |
| Role | Proxmox VE — client VM host |
| IP | 10.100.30.102 (VLAN 30 CLIENTS) |
| Wazuh Agent | 190 / ID 011 |

### SRV-01 — Services Host
| Field | Value |
|---|---|
| Model | Mac Mini (Ubuntu 22.04 LTS) |
| Role | Docker services — Wazuh, Caddy, Pi-hole, Nextcloud, Vaultwarden |
| IP | 10.100.20.101 (VLAN 20 SERVICES) |
| Wazuh Agent | SV / ID 009 |
| Notes | Primary lab services node |

### ADM-01 — Admin Workstation
| Field | Value |
|---|---|
| Model | ThinkPad T14 |
| OS | Windows 11 Pro |
| Role | Admin workstation / personal laptop |
| IP | 10.100.10.100 (VLAN 10 MGMT) |
| Wazuh Agent | T2 / ID 008 |
| ⚠️ Warning | Dual-homing risk — disable WiFi before ethernet during lab sessions |

### RED-01 — Red Team Machine
| Field | Value |
|---|---|
| Model | MacBook Pro (2012) |
| OS | Parrot OS |
| User | jcarter |
| IP | 10.100.50.100 (VLAN 50 STAGING) |
| CPU | Intel HD 3000 (SNB GT2) |
| RAM | 7.8GB |
| Battery | Degraded — replacement ordered |
| Fan Control | macfanctld installed |
| Wazuh Agent | None (intentional) |

### pfSense — Firewall
| Field | Value |
|---|---|
| Model | Running on M72e (VM currently, bare-metal planned) |
| Role | Firewall, router, DHCP, Suricata IDS |
| IP | 10.100.10.1 (VLAN 10 MGMT) |
| Notes | Phase 2: Migrate to M72e bare-metal, onboard NIC for LAN + Realtek USB NIC for WAN |

### SW-01 — Managed Switch
| Field | Value |
|---|---|
| IP | 10.100.10.239 (VLAN 10 MGMT) |
| Role | VLAN trunk / access port management |

---

## Planned Hardware

### M900 Tiny — Home Personal Server
| Field | Value |
|---|---|
| Model | Lenovo ThinkCentre M900 Tiny |
| CPU | i5-6500T |
| RAM | 8GB DDR4 (upgrade to 16GB SO-DIMM ~$25-30) |
| Internal Storage | 128GB |
| External Storage | T7 1TB SSD (photos/backups), LaCie 2TB HDD (media/music) |
| Services | Jellyfin (Intel HD 530 Quick Sync), Immich, Nextcloud |
| Access | Tailscale-only (ACLs required before go-live) |
| Notes | ~1TB archived music production files on LaCie |

### M72e — pfSense Bare-Metal (Phase 2)
| Field | Value |
|---|---|
| Role | Replace pfSense VM on HV-01 |
| NICs | Onboard NIC (LAN) + Realtek USB NIC (WAN) |

---

## Retired / Replaced Equipment

| Old Equipment | Replaced By | Notes |
|---|---|---|
| MacBook Air (2020) | SRV-01 (Mac Mini) | Now running Ubuntu/Docker |
| MacBook Pro (2012) as personal | RED-01 (Parrot OS) | Repurposed for red team |
| TP-Link AX50 | pfSense on M72e | Router replaced by pfSense |
| TP-Link AX3200 | pfSense | Option B DMZ candidate |
| Oracle VirtualBox | Proxmox VE | Full hypervisor migration |
| Mac mini (2014) | SRV-01 | Hardware upgrade |

---

## Proxmox Console Note

⚠️ **Proxmox noVNC limitation:** Shift and Ctrl keys do not work inside VM consoles. No clipboard available. Always use SSH or Proxmox node shell instead of VM console for commands requiring Shift/Ctrl.

---

## Related Notes
- [[Lab-Architecture-Overview]]
- [[HV-01]]
- [[SRV-01-Services]]
- [[RED-01]]
