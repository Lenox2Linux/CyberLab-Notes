# 🐳 SRV-01 Docker Stack

**Updated:** 2026-04-05

---

![[SRV-01-Docker-Stack.png]]

---

## Context

Service map of all Docker containers running on INTELUX-SRV-01 (Mac Mini, Ubuntu 24.04, VLAN 20 SERVICES). Shows the Caddy reverse proxy at the top routing traffic to downstream services, the Prometheus monitoring stack scraping node exporters from HV-01, CL-01, and SRV-01, and the Suricata IDS pipeline feeding EVE JSON logs from pfSense WAN into Wazuh. The syslog wrapper parsing issue (INC-004) is noted on the Suricata pipeline block.

---

## Related Notes

- [[SRV-01-Docker-Stack]]
- [[INTELUX-SRV-01 — Apple Mac Mini (Late 2014)]]
- [[Wazuh-SIEM]]
- [[Suricata-IDS]]
- [[Diagrams-Index]]