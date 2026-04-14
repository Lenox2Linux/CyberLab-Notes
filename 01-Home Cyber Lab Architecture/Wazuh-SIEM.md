# 🛡️ Wazuh SIEM — INTELUX SOC Platform

**Updated:** 2026-04-05
**Status:** Active
**Version:** 4.14.x single-node (Docker)
**Host:** INTELUX-SRV-01 (VLAN 20 SERVICES)

---

## Overview

Wazuh is the primary SIEM for the INTELUX lab. It provides log collection, file integrity monitoring, active response, and threat detection across all managed endpoints. Running as a single-node Docker deployment on SRV-01.

---

## Deployment

| Field | Value |
|---|---|
| Host | SRV-01 (Mac Mini, Ubuntu 24.04) |
| Deployment | Docker — single-node |
| Version | 4.14.x |
| Compose file | `/home/aredeebee/homelab/wazuh-docker/single-node/docker-compose.yml` |

### Containers

| Container | Port(s) | Role |
|---|---|---|
| single-node-wazuh.manager-1 | 1514, 1515, 55000 | Manager — agent comms + API |
| single-node-wazuh.dashboard-1 | 8444 | Web dashboard |
| single-node-wazuh.indexer-1 | 9200 | Indexer — log storage |

---

## Agent Registry

| Agent Name | ID | Host | OS | VLAN | Status |
|---|---|---|---|---|---|
| ADM-01 | 008 | ThinkPad T14 | Windows 11 | 10 | Active |
| SVC | 016 | SRV-01 | Ubuntu 24.04 | 20 | Active |
| HV-01 | 011 | M920q | Proxmox/Debian | 10 | Active |
| CL-01 | 012 | M910q | Proxmox/Debian | 30 | Active |
| WKS-03 | 014 | VM 101 | Windows 10 | 30 | Active (powered off) |
| WKS-04 | 015 | VM 102 | Windows 10 | 30 | Active (powered off) |
| DC-01 | TBD | VM 103 | Windows Server | 10 | Pending install |
| RED-01 | N/A | MBP 2012 | Parrot OS | 50 | No agent — OPSEC |
| RED-02 | N/A | VM 150 | Parrot OS | 50 | No agent — OPSEC |

---

## Access

| Resource | Details |
|---|---|
| Dashboard | wazuh.intelux.local (port 8444) |
| API | Port 55000 — MGMT VLAN only |
| Indexer | Port 9200 — internal only |

---

## Key Configuration

| Setting | Value |
|---|---|
| Timezone | America/New_York |
| CA cert | Mounted via `tls_trust_pool file` in Caddy |
| Agent enrollment port | 1515 |
| Agent comms port | 1514 |

---

## Suricata Pipeline

pfSense WAN Suricata → EVE JSON → rsyslog → `/var/log/suricata-pfsense.log` → Wazuh logcollector

**Status:** Logcollector confirmed analyzing file — `rule.groups: suricata` dashboard filter returning no results. Syslog wrapper format suspected as root cause. See [[Suricata-IDS]].

---

## Known False Positives (ADM-01)

| Event | Cause | Classification |
|---|---|---|
| Event 4672 | Windows Update privilege assignment | False positive — documented |
| Event 4738 | Windows Update user account changes | False positive — documented |
| Mass FIM deletions — `HKLM\CurrentControlSet\Services\` | Windows Update cleanup | False positive — documented |

---

## Detection Gaps

| Gap | Detail | Status |
|---|---|---|
| RDP access to WKS-03 not detected | Kill Chain A initial access via RDP — no Wazuh alert generated | INC-007 — pending investigation |
| Suricata rules not matching in dashboard | Syslog wrapper format blocking rule.groups filter | INC-004 — open |

---

## Useful Commands

```bash
# Reliable Wazuh restart
docker stop caddy && docker rm caddy && docker compose up -d caddy

# Check agent status
curl -k -u admin:[redacted] https://localhost:55000/agents?pretty

# Wazuh container names
single-node-wazuh.manager-1
single-node-wazuh.dashboard-1
single-node-wazuh.indexer-1
```

---

## Related Notes
- [[Trusted-Zone]]
- [[INTELUX-SRV-01 — Apple Mac Mini (Late 2014)]]
- [[Suricata-IDS]]
- [[Incidents-And-Lessons]]
- [[pfSense-Firewall]]

---
## 📚 Study Connections
| Lab Concept | Exam Topic |
|---|---|
| Wazuh as SIEM | [[Network-Security-Concepts]] |
| Log collection from agents | [[Net-3.0-Network-Operations-Hub]] |
| File integrity monitoring | [[2.0-Security-Hub]] |
| Agent comms ports 1514/1515 | [[Ports-Protocols]] |
| API port 55000 locked to MGMT VLAN | [[Network-Security-Concepts]] |
| IDS/detection gap analysis | [[Attack-Types]] |
| False positive documentation | [[4.0-Operational-Procedures-Hub]] |
| Wazuh as detective control | [[Network-Security-Concepts]] |
| Docker single-node deployment | [[4.0-Virtualization-Cloud-Hub]] |
