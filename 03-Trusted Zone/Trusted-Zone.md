# 🟢 Trusted Zone — VLAN 10 MGMT / VLAN 20 SERVICES / VLAN 30 CLIENTS

**Updated:** 2026-04-05

---

## Overview

The Trusted Zone covers all production lab infrastructure. Wazuh agents are deployed on all assets here. Access from STAGING and PORTAL is blocked or strictly controlled.

---

## VLAN 10 — MGMT

| Asset   | OS         | Role                             |
| ------- | ---------- | -------------------------------- |
| pfSense | pfSense CE | Firewall / Router                |
| HV-01   | Proxmox VE | Primary hypervisor (M920t)       |
| ADM-01  | Windows 11 | Admin workstation (ThinkPad T14) |
| SW-01   | —          | Managed switch                   |

### ADM-01 Notes
- Wazuh agent: T2 / ID 008
- Dual-homing risk: WiFi must be disabled before connecting ethernet during lab sessions
- Event 4672/4738 = Windows Update activity (not intrusion)
- Mass FIM registry deletions under `HKLM\CurrentControlSet\Services\` = Windows Update cleanup pattern

---

## VLAN 20 — SERVICES

| Asset  | OS              | Role                             |
| ------ | --------------- | -------------------------------- |
| SRV-01 | Ubuntu / Docker | Primary services host (Mac Mini) |
| DC-01  | Windows Server  | Domain Controller — **PLANNED**  |
| WEB-01 | TBD             | Internal web server              |

### SRV-01 Services

| Service         | Container Name                |
| --------------- | ----------------------------- |
| Wazuh Manager   | single-node-wazuh.manager-1   |
| Wazuh Dashboard | single-node-wazuh.dashboard-1 |
| Wazuh Indexer   | single-node-wazuh.indexer-1   |
| Caddy           | caddy                         |
| Pi-hole         | pihole                        |
| Nextcloud       | nextcloud                     |
| Vaultwarden     | vaultwarden                   |

### Key File Paths (SRV-01)
```
/home/aredeebee/homelab/docker-compose.yml
/home/aredeebee/homelab/wazuh-docker/single-node/docker-compose.yml
/home/aredeebee/homelab/caddy/Caddyfile
/var/lib/docker/volumes/homelab_nextcloud_data/_data/config/config.php
```

### Caddy Notes
- Local certs via `local_certs`
- Wazuh CA cert mounted for `tls_trust_pool file`
- `tls_insecure_skip_verify` removed
- Pi-hole DNS records pointing to 10.100.20.x
- Tailscale was overwriting `/etc/resolv.conf` — fixed with `sudo tailscale set --accept-dns=false`
- Reliable restart: `docker stop caddy && docker rm caddy && docker compose up -d caddy`
- ⚠️ Never run `docker exec caddy caddy fmt` — stderr redirect bug wipes Caddyfile to 1 byte

---

## VLAN 30 — CLIENTS

| Asset  | OS         | Role                                    |
| ------ | ---------- | --------------------------------------- |
| CL-01  | Proxmox VE | Client hypervisor (M910t)               |
| WKS-01 | TBD        | Workstation — ossec.conf update pending |
| WKS-03 | TBD        | Kill Chain A target                     |
| WKS-04 | TBD        | Out of scope (Kill Chain A)             |

---

## Wazuh Agent Registry

| Agent Name | ID | Host | OS | Status |
|---|---|---|---|---|
| T2 | 008 | ADM-01 | Windows | Active |
| SV | 009 | SRV-01 | Linux | Active |
| 290 | 010 | HV-01 | Linux | Active |
| 190 | 011 | CL-01 | Linux | Active |
| vicone | VM100 | — | — | Active |
| vicdos | VM101 | WKS-01 | — | Agent install pending (VNC console proxy issue) |

---

## Previous Trusted Zone (Phase 0)

| Old | New |
|---|---|
| Mac mini (2014) | SRV-01 (Mac Mini running Ubuntu/Docker) |
| MacBook Air (2020) | ADM-01 (ThinkPad T14, Windows 11) |
| Windows 10 Pro | Windows 11 Pro (ADM-01) |
| Mac OS 12 Monterey | Ubuntu 22.04 LTS (SRV-01) |
| Oracle VirtualBox | Proxmox VE (HV-01, CL-01) |
| Ubuntu Jammy Jellyfish (VirtualBox) | Native Docker on SRV-01 |
| No SIEM | Wazuh v4.14.3 |

---

## Related Notes
- [[Lab-Architecture-Overview]]
- [[INTELUX-SRV-01 — Apple Mac Mini (Late 2014)]]
- [[Wazuh-SIEM]]
- [[INTELUX-DC-01]]
- [[VM-Registry]]
- [[pfSense-Firewall]]