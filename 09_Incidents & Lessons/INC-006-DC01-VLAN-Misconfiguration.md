# INC-006 — DC-01 VLAN Misconfiguration

**Date:** 2026-04-05
**Status:** ✅ RESOLVED
**Severity:** Low
**System:** INTELUX-DC-01 (VM 103, HV-01)

---

## Symptom

WKS-03 (VLAN 30 CLIENTS) could not communicate with DC-01 during domain join. Domain controller was unreachable from the client subnet.

---

## Root Cause

DC-01 was initially deployed on VLAN 20 (SERVICES) at 10.100.20.102. pfSense firewall rules block lateral traffic from VLAN 30 (CLIENTS) to VLAN 20 (SERVICES) — this is by design for lab isolation. However it also prevented WKS-03 from reaching the domain controller for AD authentication and domain join operations.

---

## Fix

DC-01 moved to VLAN 10 (MGMT) at 10.100.10.102. MGMT VLAN has broader reachability across lab segments, allowing WKS-03 to communicate with DC-01 for domain operations.

---

## Lesson

Plan VLAN placement around communication requirements **before** deployment. Key questions to ask before placing any VM:

- Which VLANs need to reach this service?
- Are there existing pfSense rules blocking that traffic?
- If blocked by design, do I need a pinhole rule or should I move the VM?

Domain controllers specifically need to be reachable by all client VLANs. Options going forward:
1. Keep DC-01 on MGMT (current) — simplest
2. Move DC-01 back to SERVICES and create explicit pfSense allow rules for CLIENTS → DC-01 on required ports (88, 389, 445, 636, 3268)

---

## Current State

DC-01 on VLAN 10 MGMT (10.100.10.102) — WKS-03 domain joined to intelux.local — Administrator account active.

---

## Related Notes
- [[INTELUX-DC-01]]
- [[Trusted-Zone]]
- [[Incidents-And-Lessons]]
- [[Lab-Architecture-Overview]]
