# 🎓 Professional Development

**Updated:** 2026-04-05
**Name:** Raynard A. Porter

---

## Career Target

**Domain:** Cyber Defense Operations — SOC Analysis, Active Defense, GRC

**Target Roles:**
- SOC Analyst (Tier 1/2)
- Cyber Threat Detection / Active Defense Analyst
- GRC Analyst / Compliance Analyst
- DFIR Analyst

**Target Timeline:** Entry-level SOC or GRC role — Fall/Winter 2027 post-transfer

---

## Education

| Institution | Program | Status |
|---|---|---|
| Westchester Community College (WCC) | A.A.S. Cybersecurity | In progress — Expected Spring 2027 |
| Current semester | 3rd semester | Active |

### Academic Highlights
- PTK (Phi Theta Kappa) member
- Strong GPA

### Transfer Targets (Fall/Summer 2027)
- Penn State
- Pace University

---

## Certification Roadmap

| Cert                                 | Status      | Target      |
| ------------------------------------ | ----------- | ----------- |
| Google Cybersecurity Certificate     | In Progress | Spring 2026 |
| ISC² CC (Certified in Cybersecurity) | In Progress | Spring 2026 |
| CompTIA A+ Core 1                    | Studying    | May 2026    |
| CompTIA A+ Core 2                    | Studying    | May 2026    |
| CompTIA Network+                     | Studying    | May 2026    |
| CompTIA Security+                    | Planned     | Late 2026   |
| GIAC GCIH                            | Planned     | 2027        |
| OSCP                                 | Planned     | 2027        |

---

## Current Lab Sprint (April 2026)

### ✅ Completed This Sprint
- Suricata WAN deployment (ETOpen rules, EVE JSON pipeline)
- Vaultwarden MFA enabled
- Caddyfile review — Wazuh CA trust via `tls_trust_pool file`, `tls_insecure_skip_verify` removed
- GRC change control docs (L-1, L-2, L-6)
- RISK-001 CLOSED — PORTAL→SERVICES lateral movement mitigated
- Full VLAN migration (192.168.1.x → 10.100.x.x)
- pfSense firewall rule redesign (5 VLANs live)
- Wazuh agents reconnected post-migration
- RED-01 internet fix (rule order)

### 🔄 In Progress / Remaining MEDIUM
- DC-01 deploy (VM 101, 10.100.20.102, VLAN 20)
- East-west Docker isolation on SRV-01 (blocked — restore port bindings first)
- VLAN 60 DMZ (pfSense + SW-01 + WEB-01 at 10.100.60.10)

### 📋 LOW Priority
- Kill Chain B WEB-01 (needs VLAN 60 first)
- Friend role brief
- Option B AX3200 DMZ

---

## Portfolio Projects

### INTELUX Systems, Inc.
- Home lab modeled as enterprise cybersecurity environment
- Covers: SOC analysis, Red Team ops, GRC, network engineering, DFIR, IAM
- ISO 27001 compliance matrices, incident reports, network topology artifacts
- GitHub: [github.com/Lenox2Linux](https://github.com/Lenox2Linux)

### PhishTix
- Python/Flask phishing analysis and analyst training SaaS concept
- 5 hardcoded demo cases
- GitHub: [github.com/Lenox2Linux/phishtix](https://github.com/Lenox2Linux/phishtix)
- WCC capstone target: Spring 2027
- Public launch: Post-capstone
- Status: Running locally at http://127.0.0.1:5000

---

## Work Experience

**Operations Assistant**
New York City Department of Sanitation
- Current role

---

## GRC Alignment

| Framework | Application |
|---|---|
| ISO 27001 | Lab documentation, RISK-001 closure (A.13.1.3) |
| NIST CSF | Blue team operations reference |
| Kill Chain / ATT&CK | Red team exercise structure |

---

## Related Notes
- [[Lab-Architecture-Overview]]
- [[Incidents-And-Lessons]]
- [[PhishTix]]
