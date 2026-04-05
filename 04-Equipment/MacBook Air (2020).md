# 💻 MacBook Air (2020) — Personal Device

**Updated:** 2026-04-05 **Status:** Active — personal use **Lab Role:** Limited — Tailscale remote access only

---

## Overview

The MacBook Air (2020) is a personal machine running macOS 26 Tahoe. It is not part of the INTELUX lab infrastructure but connects to select lab services remotely via Tailscale for personal use.

---

## Hardware Specifications

|Field|Value|
|---|---|
|Model|MacBook Air (2020)|
|Chip|Apple M1|
|RAM|8 GB|
|Storage|256 GB (base config)|
|OS|macOS 26 Tahoe|

---

## Lab Connectivity

|Method|Purpose|
|---|---|
|Tailscale|Remote access to INTELUX services|
|Nextcloud|Personal file sync via `nextcloud.intelux.local`|
|General|Light personal use of self-hosted services|

---

## Security Notes

- Not a managed INTELUX endpoint
- No Wazuh agent installed
- Not on any INTELUX VLAN — Tailscale only
- Tailscale ACLs must be reviewed before M900 Tiny go-live to ensure MacBook Air is not inadvertently granted access to RED machine segments

---

## What It Is NOT Used For

- Lab management (that's ADM-01)
- Red team operations (that's RED-01)
- Any INTELUX VLAN-connected activity

---

## Related Notes

- [[Mac OS 26 Tahoe]]
- [[Equipment-Inventory]]
- [[HOME-SRV-01-M900-Tiny]]