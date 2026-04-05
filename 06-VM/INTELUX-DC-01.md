# 🏛️ INTELUX-DC-01 — Domain Controller

**Updated:** 2026-04-05
**INTELUX Role:** Active Directory Domain Controller
**Status:** Active — deployed

---

## Deployment Details

| Field       | Value                               |
| ----------- | ----------------------------------- |
| VM ID       | 103 on HV-01                        |
| Host        | INTELUX-HV-01 (M920q)               |
| OS          | Windows Server 2022                 |
| VLAN        | 10 — MGMT (see incident note below) |
| Wazuh Agent | Pending install                     |

---

## Active Directory

| Field        | Value                                                              |
| ------------ | ------------------------------------------------------------------ |
| Domain Users | Administrator                                                      |
| Purpose      | AD DS, domain auth, Kill Chain A crown jewel, general AD education |

---

## Deployment Incident — VLAN Assignment

**Issue:** DC-01 was originally placed on VLAN 20 (SERVICES). WKS-03 on VLAN 30 (CLIENTS) could not communicate with DC-01 for domain join operations — cross-VLAN traffic between CLIENTS and SERVICES is blocked by pfSense firewall rules.

**Fix:** DC-01 moved to VLAN 10 (MGMT) at 10.100.10.x. MGMT VLAN has broader reachability across the lab, allowing WKS-03 to communicate with the domain controller.

**Lesson:** Plan VLAN placement around communication requirements before deployment. Domain controllers need to be reachable by all client VLANs — either place DC in a reachable VLAN or create explicit pfSense rules allowing CLIENTS → DC-01 traffic before deploy.

---

## WKS-03 Domain Join

| Field | Value |
|---|---|
| Machine | INTELUX-WKS-03 (VM 101, VLAN 30) |
| Domain | intelux.local |
| Username used | Administrator |
| Purpose | Kill Chain A preparation + general AD education |
| Wazuh Agent | Agent 014 — still active |

---

## Pending

- [ ] Wazuh agent install on DC-01
- [ ] Additional domain users for Kill Chain A scenario
- [ ] Group Policy configuration
- [ ] DNS verification — DC-01 as authoritative DNS for intelux.local

---

## Kill Chain A Relevance

DC-01 serves as the **crown jewel** target for Kill Chain A. The exercise objective is:

```
RED-01 (VLAN 50) → WKS-03 (VLAN 30) → DC-01 (VLAN 10)
```

WKS-03 is now domain-joined to `intelux.local`, making it a realistic pivot point for credential harvesting and lateral movement toward DC-01.

---

## Related Notes
- [[VM-Registry]]
- [[Trusted-Zone]]
- [[Kill-Chain-A-Flow]]
- [[INTELUX-HV-01-M920t]]
- [[Incidents-And-Lessons]]
