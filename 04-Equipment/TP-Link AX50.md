# 📡 TP-Link AX50 — Lab Uplink Router

**Updated:** 2026-04-05 **Status:** Active — lab WAN uplink **Lab Role:** Provides internet feed from AX3200 into pfSense

---

## Overview

The TP-Link AX50 sits between the home gateway (AX3200) and the INTELUX pfSense firewall. It passes internet connectivity from the AX3200 into the lab network. pfSense (VM on HV-01) handles all firewall, VLAN routing, and security functions — the AX50 is purely an uplink device in this architecture.

---

## Network Role

```
[TP-Link AX3200] ← Home gateway / ISP feed
  │
[TP-Link AX50]   ← Lab uplink — passes WAN to pfSense
  │
[pfSense VM — HV-01] ← INTELUX firewall / VLAN router
  │
[INTELUX VLANs]
```

---

## Device Details

|Field|Value|
|---|---|
|Model|TP-Link AX50|
|Role|Lab WAN uplink router|
|WAN Source|TP-Link AX3200 (home gateway)|
|WAN Destination|pfSense VM on HV-01|
|INTELUX VLAN|None — upstream of pfSense|
|Wazuh Agent|None|

---

## Phase 0 Reference

In Phase 0, the AX50 was deployed in router-behind-router mode to create a Double NAT isolation barrier between the lab and the trusted home network. It was the primary lab isolation mechanism before pfSense replaced it in that role.

The AX50's security and isolation responsibilities have been fully handed off to pfSense. Its current role is simply passing WAN connectivity into the lab.

---

## Planned Changes

When pfSense migrates from VM (HV-01) to bare-metal M72e, the AX50 remains in place — same uplink role, new downstream device.

---

## Related Notes

- [[TP-Link AX3200]]
- [[INTELUX-FW-01-M72e-Planned]]
- [[Lab-Architecture-Overview]]
- [[(Phase 0) Multi-Tiered Defensive Architecture & Cybersecurity Lab Isolation]]