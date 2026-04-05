# 🖥️ INTELUX-SRV-01 — Apple Mac Mini (Late 2014)

**Updated:** 2026-04-05 **INTELUX Role:** Primary Services Host **Status:** Active

---

## Acquisition & Evolution

|Phase|Role|OS|
|---|---|---|
|Phase 0|Virtualization host (VirtualBox)|macOS / Ubuntu VM|
|Phase 1+ (Current)|Docker services host|Ubuntu 24.04 LTS|

---

## Hardware Specifications

|Field|Value|
|---|---|
|Model|Apple Mac Mini (Late 2014)|
|CPU|Intel Core i5-4278U @ 2.6GHz (2C/4T)|
|RAM|8 GB DDR3 1600 MT/s (2x4GB SK Hynix — 0 slots open, soldered)|
|Storage|931.5 GB HDD (2.5" SATA — only slot, no NVMe)|
|Max RAM|16 GB (replace both sticks — 2x8GB DDR3 1600)|
|OS|Ubuntu 24.04 LTS|

---

## Docker Services

| Service         | Status |
| --------------- | ------ |
| Wazuh Manager   | Active |
| Wazuh Dashboard | Active |
| Wazuh Indexer   | Active |
| Caddy           | Active |
| Pi-hole         | Active |
| Grafana         | Active |
| Prometheus      | Active |
| Nextcloud       | Active |
| Vaultwarden     | Active |
| Portainer       | Active |
| Uptime Kuma     | Active |

---

## Known Issues & Workarounds

|Issue|Fix|
|---|---|
|Tailscale overwriting /etc/resolv.conf|`sudo tailscale set --accept-dns=false`|
|Caddy `docker exec caddy caddy fmt` wipes Caddyfile|Never use — backup first, use restart workaround|
|Caddy restart (containerd unmount bug)|`docker stop caddy && docker rm caddy && docker compose up -d caddy`|

---

## Related Notes

- [[Trusted-Zone]]
- [[Wazuh-SIEM]]
- [[Lab-Architecture-Overview]]
- [[Incidents-And-Lessons]]