# 📋 Incidents & Lessons Learned

**Updated:** 2026-04-05

---

## Closed Incidents

---

### RISK-001 — PORTAL→SERVICES Lateral Movement
**Date Closed:** 2026-03-31
**Severity:** Medium
**Status:** ✅ CLOSED

**Finding:** PORTAL VLAN (40) had unrestricted access to SERVICES VLAN (20), enabling potential lateral movement from kiosk to internal services.

**Mitigation:**
- TCP 443 pinhole created to WEB-01 (10.100.20.103) only
- Rest of SERVICES blocked from PORTAL
- ISO 27001 control satisfied: **A.13.1.3**

**GRC docs:** L-1, L-2, L-6 filed. Change control documented.

---

### INC-001 — RED-01 Internet Access Failure
**Date:** 2026-04-02
**Status:** ✅ RESOLVED

**Symptom:** RED-01 (10.100.50.100) had no internet access despite firewall intent to allow it.

**Root Cause:** pfSense STAGING rule order — "Block Lab_Subnets" rule was positioned **above** ICMP/egress allow rules. pfSense processes rules top-down; the block rule was matching before the allow rules fired.

**Fix:** Reordered rules — allow rules moved above block rule. Internet C2 alt rule re-enabled. Lab isolation confirmed intact.

**Lesson:** pfSense rule order is critical. Always verify rule ordering after any firewall change. Use the pfSense rule tester to validate traffic flow.

---

### INC-002 — Caddy Caddyfile Wiped to 1 Byte
**Date:** 2026-03~ (during Caddy config work)
**Status:** ✅ RESOLVED (file rewritten)

**Symptom:** Running `docker exec caddy caddy fmt` caused Caddyfile to be wiped to 1 byte.

**Root Cause:** stderr redirect bug in `caddy fmt` command when executed via `docker exec`. Output was written back over the Caddyfile path instead of stdout.

**Fix:** Caddyfile fully rewritten from memory/backups.

**Lesson:** Never run `docker exec caddy caddy fmt` without first backing up the Caddyfile. Reliable Caddy restart method:
```bash
docker stop caddy && docker rm caddy && docker compose up -d caddy
```
Do not use `--force-recreate` (persistent containerd unmount bug).

---

### INC-003 — Tailscale Overwriting /etc/resolv.conf
**Date:** 2026-03~
**Status:** ✅ RESOLVED

**Symptom:** Caddy and other services on SRV-01 failing DNS resolution for `*.intelux.local`. Pi-hole DNS records not being used.

**Root Cause:** Tailscale was overwriting `/etc/resolv.conf` with its own DNS, bypassing Pi-hole.

**Fix:**
```bash
sudo tailscale set --accept-dns=false
```

**Lesson:** Tailscale DNS takeover is a known issue on Linux. Always disable `accept-dns` on nodes where local DNS (Pi-hole, custom resolvers) must take priority.

---

### INC-004 — Suricata EVE JSON Not Matching Wazuh Rules
**Date:** 2026-04-03~
**Status:** 🔴 OPEN — Pending

**Symptom:** rsyslog on port 5140 writing to `/var/log/suricata-pfsense.log`, Wazuh logcollector confirmed analyzing the file, but `rule.groups: suricata` dashboard filter returns no results.

**Root Cause (suspected):** Syslog wrapper format is wrapping EVE JSON in a syslog envelope that prevents correct Wazuh rule matching.

**Next steps:** Strip syslog wrapper, or write a custom Wazuh decoder for the wrapped format.

---

### INC-005 — Telegram Bot HTTP 429 Rate Limit
**Date:** 2026-04~
**Status:** 🟡 BACKLOG

**Symptom:** Telegram bot generating HTTP 429 (Too Many Requests) errors from alert backlog.

**Next steps:** Implement rate limiting / batching in bot script.

---

## False Positive Documentation

| Event | System | Explanation |
|---|---|---|
| Event 4672 on T2 (ADM-01) | Wazuh | Windows Update activity — not intrusion |
| Event 4738 on T2 (ADM-01) | Wazuh | Windows Update activity — not intrusion |
| Mass FIM registry deletions under `HKLM\CurrentControlSet\Services\` | Wazuh | Windows Update cleanup pattern — expected |

---

## Lessons Summary

| # | Lesson | Context |
|---|---|---|
| 1 | pfSense rule order is top-down — verify ordering after every change | INC-001 |
| 2 | Never run `caddy fmt` via docker exec without a backup | INC-002 |
| 3 | Tailscale overwrites resolv.conf — disable accept-dns on DNS-sensitive nodes | INC-003 |
| 4 | Syslog-wrapped JSON can break SIEM rule matching | INC-004 |
| 5 | Proxmox noVNC: Shift/Ctrl non-functional — use SSH always | Lab operations |
| 6 | Windows Update generates high-volume FIM + privilege events — document as known FP | Alert triage |

---

## Related Notes
- [[Multi-Tiered-Defensive-Architecture]]
- [[Wazuh-SIEM]]
- [[Suricata-IDS]]
- [[pfSense-Firewall]]
