## **Project Overview**

Designed and implemented a Defense in Depth network architecture to segment a high-risk cybersecurity research lab from a primary residential network. The goal was to establish a “one-way mirror” environment where [[(Phase 0) Isolated Zone]] and IoT systems remain fully functional but are logically and physically prevented from lateral movement into the [[(Phase 0) Trusted Zone]] network.

As part of this build, I repurposed legacy hardware into dedicated lab systems, including my [[Kali Cyber Lab Rebuild]] to serve as a controlled attack node inside the isolated environment.

---

## **Technical Implementation**

### **Hardware & Topology Phase**

- **Gateway Overhaul:** Replaced restrictive ISP equipment with a [[TP-Link AX3200]] as the primary gateway for the trusted zone.
- **Tiered Segmentation:** Deployed a [[TP-Link AX50]] in a “router-behind-router” configuration to create a Double NAT isolation layer.
- **Dedicated Lab Systems:** Rebuilt legacy machines into hardened lab endpoints to avoid mixing personal and experimental workloads.
---

### **Lab Equipment**

- [[Mac mini (2014)]] — Virtualization host
- [[MacBook Pro (2012)]] — Kali lab workstation
- [[TP-Link AX50]] — Lab router
- [[TP-Link AX3200]] — Primary gateway

---

### **System Rebuild & OS Deployment Phase**

To ensure the lab environment started from a known, trusted baseline, I rebuilt the MacBook Pro (2012) from scratch.

I first downloaded the macOS Monterey installer and created a bootable USB using Terminal’s `createinstallmedia` utility. After validating the installer media, I wiped the internal drive using Disk Utility to remove all residual data and configurations.

Once macOS recovery and disk preparation were complete, I flashed an Ubuntu installation image to a USB drive using BalenaEtcher and configured the system to boot from external media. I then performed a clean Ubuntu installation, creating a dedicated Linux workstation for administration, monitoring, and controlled attack simulations.

Post-installation validation included verifying network interfaces, IP assignment, hostname identity, and system stability using `ip a`, hostname prompts, and connectivity tests.

This ensured the lab workstation operated from a clean baseline and reduced the risk of inherited misconfigurations affecting later experiments.

---

## **Walkthrough**

Most home networks are flat and minimally segmented. If an IoT device, virtual machine, or lab system is compromised, an attacker can move laterally to personal devices without resistance.

To eliminate this risk, I transitioned from a single-point-of-failure network to a tiered defense architecture.

I began by replacing the ISP-issued router with a TP-Link AX3200 as the primary gateway. After a factory reset, I hardened the trusted zone by enforcing WPA3/WPA2-AES encryption, disabling WPS and UPnP, and configuring DHCP reservations to keep infrastructure addressing stable.

For lab isolation, I deployed a TP-Link AX50 in router mode. Connecting its WAN port to the primary LAN created a Double NAT barrier. This functions as a one-way mirror: the lab can reach the internet for updates, but the trusted zone cannot see into the lab network. I verified this using ICMP testing, which resulted in 100% packet loss from the trusted zone to the lab segment.

Inside the lab, I implemented additional controls:

- MAC address whitelisting to restrict device enrollment
- IP/MAC binding to prevent ARP spoofing
- Static IP assignments for critical systems
- Dual-adapter VM configurations (NAT + Internal Network)
- Dedicated Linux workstations for attack and monitoring roles

The rebuilt MacBook Pro running Kali was anchored to the internal segment and used for reconnaissance, testing, and system administration without exposing personal devices.

---

## **Virtualization & Micro-Segmentation**

The Mac mini was configured as a virtualization host using VirtualBox. I deployed Ubuntu and Windows 10 virtual machines with dual network adapters:

- NAT adapter for secure internet access and updates
- Internal Network adapter for isolated lab communication

This allowed safe red/blue team simulations while maintaining full containment.

Static addressing on the internal segment ensured consistent VM-to-VM connectivity and simplified troubleshooting.

---

## **Validation & Testing**

- Verified Double NAT isolation using ICMP and traceroute
- Confirmed Ubuntu workstation identity and network configuration
- Validated VM communication on internal network
- Tested firewall boundaries between zones
- Audited DHCP and reservation behavior
- Confirmed absence of lateral movement paths
---

## **Lessons Learned**

- Clean system baselines significantly reduce long-term troubleshooting
- Physical and virtual segmentation must work together
- Rebuilding legacy hardware extends its operational value
- Boot media creation and disk wiping are foundational IT skills
- Post-install validation prevents silent misconfigurations
- Defense in depth is most effective when implemented end-to-end

---

## **Final Result**

The final environment is a hardened, tiered security architecture.

IoT devices operate behind multiple firewalls. Lab experiments remain contained within segmented physical and virtual networks. Dedicated Linux systems handle testing and monitoring. Personal data and trusted systems remain unreachable from the lab.

The infrastructure functions as a controlled sandbox for cybersecurity experimentation, system administration practice, and defensive research.