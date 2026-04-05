# 🖧 VM Registry

**Updated:** 2026-04-05

---

## HV-01 VMs (Proxmox — 10.100.10.101)

| VM ID | Name | IP | VLAN | OS | Status |
|---|---|---|---|---|---|
| 100 | vicone | — | — | TBD | Active |
| 101 | vicdos / WKS-01 | 10.100.10.102 | 10 | TBD | Wazuh agent install pending |
| TBD | DC-01 | 10.100.20.102 | 20 | Windows Server 2022 | **Planned** |
| TBD | WEB-01 | 10.100.20.103 / 10.100.60.10 | 20/60 | TBD | Planned |

---

## CL-01 VMs (Proxmox — 10.100.30.102)

| VM ID | Name | IP | VLAN | OS | Status |
|---|---|---|---|---|---|
| TBD | WKS-03 | 10.100.30.11 | 30 | TBD | Kill Chain A target — active |
| TBD | WKS-04 | TBD | 30 | TBD | Out of scope |

---

## SRV-01 Containers (Docker — 10.100.20.101)

| Container | Image | Port(s) | Status |
|---|---|---|---|
| single-node-wazuh.manager-1 | wazuh/wazuh-manager | 1514, 1515, 55000 | Active |
| single-node-wazuh.dashboard-1 | wazuh/wazuh-dashboard | 8444 | Active |
| single-node-wazuh.indexer-1 | wazuh/wazuh-indexer | 9200 | Active |
| caddy | caddy | 80, 443 | Active |
| pihole | pihole/pihole | 53, 8080 | Active |
| nextcloud | nextcloud | — | Active |
| vaultwarden | vaultwarden/server | — | Active |

### Wazuh Version
`v4.14.3`

---

## Pending VM Actions

| VM | Action | Blocker |
|---|---|---|
| WKS-01 (VM101) | Update ossec.conf manager IP to 10.100.20.101 | VNC console proxy issue (Proxmox noVNC) |
| DC-01 | Full deploy — AD DS, DNS, GP | Not yet built |
| WEB-01 | Deploy to VLAN 20 + VLAN 60 DMZ | VLAN 60 not yet configured |

---

## Proxmox Console Warning

⚠️ Proxmox noVNC: **Shift and Ctrl keys do not function** in VM consoles. No clipboard available.
Always use SSH or Proxmox node shell for any commands requiring modifier keys.

---

## DC-01 Setup Reference

- **VM:** 101, IP: 10.100.20.102, VLAN 20
- **Lab password (DSRM + setup, no special chars):** `=password4intelux26=`
- **Post-deploy:** Install Wazuh agent, join to intelux.local domain

---

## Related Notes
- [[Equipment-Inventory]]
- [[Trusted-Zone]]
- [[DC-01-Deploy]]
- [[Wazuh-SIEM]]
