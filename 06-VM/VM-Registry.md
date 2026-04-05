# 🖧 VM Registry

**Updated:** 2026-04-05

---

## HV-01 VMs (Proxmox — MGMT VLAN)

|VM ID|Name|VLAN|OS|Status|
|---|---|---|---|---|
|100|INTELUX-FW-01|All|pfSense CE 2.7.2|Active|
|101|WKS-03|30|Windows 10 Pro|Active — domain joined|
|102|WKS-04|30|Windows 10 Pro|Active (powered off)|
|103|DC-01|10|Windows Server 2022|✅ Active — deployed|
|104|WEB-01|20/60|Debian Linux|Planned|
|105|KSK-01|40|Debian minimal|Planned|
|150|RED-02|50|Parrot OS|Planned|

---

## CL-01 VMs (Proxmox — CLIENTS VLAN)

|VM ID|Name|VLAN|OS|Status|
|---|---|---|---|---|
|200|WKS-05|30|Windows 10 Pro|Planned|
|201|WKS-06|30|Windows 10 Pro|Planned|
|250|HNY-01|50|TBD (Honeypot)|Future|

---

## SRV-01 Containers (Docker — SERVICES VLAN)

|Container|Image|Status|
|---|---|---|
|single-node-wazuh.manager-1|wazuh/wazuh-manager|Active|
|single-node-wazuh.dashboard-1|wazuh/wazuh-dashboard|Active|
|single-node-wazuh.indexer-1|wazuh/wazuh-indexer|Active|
|caddy|caddy|Active|
|pihole|pihole/pihole|Active|
|grafana|grafana|Active|
|prometheus|prom/prometheus|Active|
|nextcloud|nextcloud|Active|
|vaultwarden|vaultwarden/server|Active|
|portainer|portainer/portainer-ce|Active|
|uptime-kuma|louislam/uptime-kuma|Active|

### Wazuh Version

`v4.14.3`

---

## DC-01 — Active Directory

|Field|Value|
|---|---|
|VM ID|103 on HV-01|
|VLAN|10 — MGMT|
|OS|Windows Server 2022|
|Domain|intelux.local|
|Domain Users|Administrator|
|Wazuh Agent|Pending install|
|Status|Active — deployed 2026-04-05|

> ⚠️ DC-01 was originally placed on VLAN 20 SERVICES — moved to VLAN 10 MGMT after WKS-03 could not reach it for domain join. See [[INC-006-DC01-VLAN-Misconfiguration]].

---

## Pending VM Actions

|VM|Action|Blocker|
|---|---|---|
|WKS-01|Update ossec.conf manager IP|VNC console proxy issue (Proxmox noVNC)|
|DC-01|Install Wazuh agent|Pending|
|DC-01|Group Policy configuration|Pending|
|WEB-01|Deploy to VLAN 20 + VLAN 60 DMZ|VLAN 60 not yet configured|
|KSK-01|Deploy to VLAN 40|WEB-01 must be built first|

---

## Proxmox Console Warning

⚠️ Proxmox noVNC: **Shift and Ctrl keys do not function** in VM consoles. No clipboard available. Always use SSH or Proxmox node shell for any commands requiring modifier keys.

---

## Related Notes

- [[INTELUX-DC-01]]
- [[Equipment-Inventory]]
- [[Trusted-Zone]]
- [[Wazuh-SIEM]]
- [[INC-006-DC01-VLAN-Misconfiguration]]