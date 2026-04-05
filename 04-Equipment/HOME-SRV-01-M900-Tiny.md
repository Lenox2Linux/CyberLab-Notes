# 🏠 HOME-SRV-01 — Lenovo ThinkCentre M900 Tiny

**Updated:** 2026-04-05
**Role:** Personal Home Server (outside INTELUX lab scope)
**Status:** Incoming — Mercari purchase

---

## Acquisition

- **Source:** Mercari
- **Current OS:** Windows 10 (will be wiped)

---

## Hardware Specifications

| Field | Value |
|---|---|
| Model | Lenovo ThinkCentre M900 Tiny |
| CPU | Intel Core i5-6500T (Intel HD 530 — Quick Sync capable) |
| RAM | 8 GB DDR4 SO-DIMM (upgrade planned) |
| Internal Storage | 128 GB |
| External Storage 1 | T7 1TB SSD — photos / Immich / backups |
| External Storage 2 | LaCie 2TB HDD — media / music (~1TB archived music production files) |
| Max RAM | 32 GB DDR4 SO-DIMM |

---

## RAM Upgrade

| Field | Value |
|---|---|
| Upgrade | 16 GB DDR4 SO-DIMM (replace 8GB stick) |
| Est. Cost | ~$25–30 |
| Priority | Before go-live |

---

## Planned Services

| Service | Purpose | Notes |
|---|---|---|
| Jellyfin | Media server | Intel HD 530 Quick Sync for hardware transcoding |
| Immich | Photo backup / management | T7 1TB SSD as photo storage |
| Nextcloud | Personal file sync | Separate from INTELUX lab Nextcloud |
| Wazuh Agent | Endpoint monitoring | Reports to INTELUX SRV-01 Wazuh manager |
| Uptime Kuma | Service monitoring | Monitor all home server services |
| Arr Stack | Media automation | Sonarr, Radarr, Prowlarr — media management |

---

## Remote Access

- **Method:** Tailscale only — no open ports, no public exposure
- **Requirement:** Tailscale ACLs must be configured before go-live
- **Critical:** ACLs must isolate RED-01 from home server devices

---

## Deployment Plan

### Phase 1 — Base Setup
1. Receive M900 — verify hardware health
2. RAM upgrade — install 16GB DDR4 SO-DIMM
3. Wipe Windows 10 — install Ubuntu Server LTS
4. Install Docker + Docker Compose
5. Configure Tailscale — set `accept-dns=false`
6. Configure Tailscale ACLs (RED machine isolation)

### Phase 2 — Services
7. Deploy Jellyfin — configure Intel HD 530 Quick Sync
8. Deploy Immich — point to T7 1TB SSD
9. Deploy Nextcloud — personal use only
10. Deploy Uptime Kuma
11. Deploy Arr stack
12. Install Wazuh agent — enroll to SRV-01 manager

### Phase 3 — Validation
13. Verify Tailscale access from ADM-01 and mobile
14. Verify RED machine isolation via ACL test
15. Verify Quick Sync transcoding in Jellyfin
16. Verify Wazuh agent active in dashboard

---

## Notes

- This is a **personal home server** — separate from INTELUX lab infrastructure
- LaCie 2TB contains ~1TB of archived music production files — handle with care
- Intel HD 530 supports Quick Sync hardware transcoding — critical for Jellyfin performance on low-power CPU
- Wazuh agent enrollment is the only connection point to INTELUX infrastructure

---

## Related Notes
- [[Lab-Architecture-Overview]]
- [[Trusted-Zone]]
- [[Professional-Development]]
