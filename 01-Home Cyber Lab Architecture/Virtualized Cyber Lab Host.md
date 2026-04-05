
## **Project Overview**

Modernized a legacy [[Mac mini (2014)]] into a dedicated virtualization host to support a controlled cybersecurity lab environment. The goal was to create an isolated platform for attack-and-defense testing using [[Ubuntu Jammy Jellyfish]] and [[Windows 10 Pro]] virtual machines while maintaining strict separation from personal and production systems.

This project focused on rebuilding the host system, deploying a stable hypervisor, designing segmented virtual networks, and validating secure VM-to-VM communication for red/blue team exercises.

---

## **Technical Implementation**

## **Hardware & Host Preparation Phase**

- Repurposed a Mac mini (2014) as a dedicated lab server
- Performed a clean macOS installation to establish a known baseline
- Applied system updates and stability checks
- Disabled unnecessary background services
- Reserved storage and memory resources for virtualization workloads
---

## **Virtualization Platform**

- Host OS: [[Mac OS 12 Monterey]]
- Hypervisor: [[Oracle VirtualBox]]
- Guest OS:
    
    - [[Ubuntu Jammy Jellyfish]] (Attack/Admin VM)
    
    - [[Windows 10 Pro]] (Victim/Test VM)
    

---

## **Host System Rebuild & Configuration**

To ensure long-term stability, I rebuilt the Mac mini from a clean operating system baseline.

After reinstalling macOS, I validated disk health, network connectivity, and system performance. Once the host environment was stable, I installed VirtualBox and configured system permissions to support bridged and internal networking.

Resource allocation was tuned to balance performance and isolation, including dedicated RAM, CPU cores, and storage volumes for each virtual machine.

---

## **Virtual Machine Deployment Phase**

### **Ubuntu (Attack / Administration VM)**

- Installed Ubuntu from official ISO media
- Hardened baseline configuration
- Installed security and networking tools
- Configured SSH and administrative access
- Verified interface behavior and routing

### **Windows 10 (Victim / Test VM)**

- Installed Windows 10 in evaluation mode
- Applied initial system updates
- Configured default services
- Established baseline vulnerabilities for testing
- Verified logging and event collection


Each VM was snapshotted after initial configuration to enable rapid rollback and repeatable testing.

---

## **Network Architecture & Segmentation**

To prevent uncontrolled exposure, I implemented a dual-network adapter design for each virtual machine:

### **Adapter 1 — NAT**

- Provides outbound internet access
- Supports system updates and package management
- Prevents inbound connections from external networks


### **Adapter 2 — Internal Network**

- Creates a private, isolated lab segment
- Enables VM-to-VM communication
- Blocks access from the host and external systems


This design allowed controlled attack simulations without risking leakage into trusted environments.

---

## **IP Addressing & Identity Management**

On the internal network, I implemented a structured addressing scheme:

- Static or reserved IPs for critical VMs
- Verified assignments using `ip a`, `ipconfig`, and `nmcli`
- Configured hostname conventions
- Documented MAC and interface mappings


This ensured predictable connectivity and simplified troubleshooting during exercises.

---

## **Walkthrough**

Rather than running experiments directly on personal hardware, I created a dedicated virtualization host to separate learning environments from daily-use systems.

I began by rebuilding the Mac mini to remove legacy configurations and establish a stable foundation. Once the host was validated, I installed VirtualBox and configured resource pools for guest machines.

Next, I deployed Ubuntu and Windows 10 virtual machines and configured them with dual network interfaces. NAT provided safe internet access, while the Internal Network created a closed testing environment.

I verified isolation by attempting cross-segment communication and confirmed that internal traffic remained contained. Only approved paths were reachable, and no unintended routing existed between the lab and trusted networks.

Snapshots were taken at major milestones, allowing fast recovery after destructive testing.

---

## **Validation & Testing**

- Confirmed outbound connectivity via NAT
- Verified internal network isolation
- Tested Ubuntu-to-Windows communication
- Validated firewall behavior
- Confirmed snapshot recovery
- Audited routing tables and interface priorities
- Tested service exposure boundaries

---

## **Lessons Learned**

- Dedicated virtualization hosts improve security and stability
- Dual-adapter designs simplify safe testing
- Snapshot discipline enables rapid iteration
- Resource planning prevents host performance degradation
- Internal networks are essential for realistic lab simulations
- Documentation reduces rebuild time

---

## **Final Result**

The completed system functions as a secure, repeatable virtualization platform.

The Mac mini serves as a stable hypervisor host. Ubuntu provides administrative and attack tooling. Windows 10 operates as a controlled victim system. Network segmentation ensures experiments remain contained.

This environment supports malware analysis, penetration testing practice, system hardening exercises, and defensive monitoring without risking production systems.

---

## **Future Enhancements**

- Integrate centralized logging (SIEM-lite)
- Deploy IDS/IPS sensors
- Automate VM provisioning
- Add domain controller testing
- Expand to multi-subnet scenarios