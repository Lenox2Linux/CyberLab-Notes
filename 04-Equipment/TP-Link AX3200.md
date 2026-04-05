# 📡 TP-Link AX3200 — Home Gateway

**Updated:** 2026-04-05 **Status:** Active — personal home network **Lab Role:** None directly — WAN uplink source for AX50

---

## Overview

The TP-Link AX3200 serves as the primary home network gateway. It provides internet to the household and acts as the upstream WAN source for the TP-Link AX50, which feeds into the INTELUX lab network.

---

## Network Role

```
[ISP]
  │
[TP-Link AX3200] ← Home gateway / primary router
  │
[TP-Link AX50]   ← Lab uplink (WAN feed into lab segment)
  │
[pfSense VM on HV-01] ← INTELUX firewall
  │
[INTELUX VLANs 10/20/30/40/50/60]
```

---

## Device Details

|Field|Value|
|---|---|
|Model|TP-Link AX3200|
|Role|Primary home gateway|
|Provides|Internet to home network + WAN uplink to AX50|
|Lab Integration|Indirect — upstream of AX50|
|INTELUX VLAN|None|
|Wazuh Agent|None|

---

## Phase 0 Reference

In Phase 0, the AX3200 was the primary gateway for the trusted zone in the Double NAT architecture. That role has been superseded by pfSense (VM on HV-01) as the INTELUX firewall, but the AX3200 remains as the home ISP gateway upstream of the entire lab.

---

## Planned Changes

When pfSense migrates to bare-metal M72e, the upstream topology remains the same — AX3200 → AX50 → M72e (pfSense bare-metal).

---

## Related Notes

- [[TP-Link AX50]]
- [[INTELUX-FW-01-M72e-Planned]]
- [[Lab-Architecture-Overview]]