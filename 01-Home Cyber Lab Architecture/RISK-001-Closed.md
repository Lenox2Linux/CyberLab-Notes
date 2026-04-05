# 🔒 RISK-001 — PORTAL→SERVICES Lateral Movement

**Date Opened:** 2026-03~
**Date Closed:** 2026-03-31
**Status:** ✅ CLOSED
**Severity:** Medium
**Owner:** aredeebee

---

## Risk Statement

PORTAL VLAN (40) had unrestricted access to SERVICES VLAN (20), enabling potential lateral movement from a compromised kiosk endpoint directly into internal lab services including Wazuh, Nextcloud, Vaultwarden, and the planned DC-01.

---

## Affected Assets

| Asset | VLAN | Risk |
|---|---|---|
| INTELUX-KSK-01 | 40 PORTAL | Potential attacker pivot point |
| INTELUX-SRV-01 | 20 SERVICES | Exposed to unrestricted PORTAL traffic |
| INTELUX-DC-01 | 10 MGMT | Reachable via SERVICES pivot |
| Wazuh dashboard | 20 SERVICES | Admin interface exposed |
| Vaultwarden | 20 SERVICES | Password manager exposed |

---

## Mitigation Applied

**pfSense firewall rule — PORTAL → SERVICES:**
- TCP 443 pinhole to WEB-01 only — all other SERVICES traffic blocked from PORTAL
- Rule implemented and verified via pfSense rule tester
- Remaining SERVICES assets confirmed unreachable from PORTAL VLAN

**Compliance:** ISO 27001 A.13.1.3 — Segregation in networks ✅

---

## GRC Documentation

Change control documents filed: L-1, L-2, L-6

---

## Verification

Post-mitigation testing confirmed:
- PORTAL → WEB-01 TCP 443: **Allowed** (by design)
- PORTAL → SRV-01 (all other ports): **Blocked**
- PORTAL → DC-01: **Blocked**
- PORTAL → Wazuh dashboard: **Blocked**

---

## Kill Chain B Relevance

RISK-001 mitigation is the **defensive control** that Kill Chain B is designed to test. The exercise objective is to determine whether the TCP 443 pinhole to WEB-01 can be leveraged to pivot further into SERVICES despite the block rules.

```
KSK-01 (PORTAL) ──TCP 443──► WEB-01 (SERVICES) ──exploit──► DC-01
                    ↑
              only allowed path
```

See [[Kill-Chain-B-Flow]] for full exercise plan.

---

## Related Notes
- [[Multi-Tiered-Defensive-Architecture]]
- [[pfSense-Firewall]]
- [[Incidents-And-Lessons]]
- [[Kill-Chain-B-Flow]]
- [[Lab-Architecture-Overview]]
