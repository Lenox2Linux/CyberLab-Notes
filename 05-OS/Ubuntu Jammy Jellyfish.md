# 🐧 Ubuntu — INTELUX-SRV-01

**Updated:** 2026-04-05 **Status:** Active — primary services OS

---

> [!NOTE] Version Update The original note referenced Ubuntu 22.04 LTS (Jammy Jellyfish). SRV-01 is now running **Ubuntu 24.04 LTS (Noble Numbat)** per current CMDB.

---

## Deployment

|Field|Value|
|---|---|
|Host|SRV-01 (Mac Mini Late 2014)|
|Version|Ubuntu 24.04 LTS (Noble Numbat)|
|Role|Docker services host|
|VLAN|20 — SERVICES|
|IP|10.100.20.101|

---

## Services Running on Ubuntu 24.04

| Service                 | Purpose                                  |
| ----------------------- | ---------------------------------------- |
| Docker + Docker Compose | Container runtime for all lab services   |
| Wazuh Stack             | SIEM — Manager, Dashboard, Indexer       |
| Caddy                   | Reverse proxy — `*.intelux.local`        |
| Pi-hole                 | DNS filtering + forced DNS for all VLANs |
| Grafana                 | Infrastructure monitoring dashboards     |
| Prometheus              | Metrics collection                       |
| Nextcloud               | Internal file sync                       |
| Vaultwarden             | Self-hosted password manager             |
| Portainer               | Docker management UI                     |
| Uptime Kuma             | Service uptime monitoring                |
| Tailscale               | Subnet router                            |

---

## Key Configuration Notes

|Setting|Value|
|---|---|
|Tailscale DNS override|`sudo tailscale set --accept-dns=false`|
|Timezone|America/New_York|
|Wazuh version|4.14.x|

---

## Previous Version (Phase 0 Reference)

|Old|New|
|---|---|
|Ubuntu 22.04 LTS (Jammy Jellyfish) — VirtualBox VM|Ubuntu 24.04 LTS (Noble Numbat) — bare metal|
|Mac mini running macOS|Mac mini running Ubuntu|
|VirtualBox-based workloads|Native Docker stack|

---

## Related Notes

- [[INTELUX-SRV-01-MacMini]]
- [[Trusted-Zone]]
- [[Wazuh-SIEM]]
- [[OS-Registry]]