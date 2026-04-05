

## **Project Overview**

Converted a [[INTELUX-RED-01 — Apple MacBook Pro (2012)]] into a dedicated [[Kali Linux]] lab workstation for Linux administration and cybersecurity practice. The objective was to establish a clean, repeatable baseline system for controlled experimentation, tooling practice, and operating system hardening.

This project focused on rebuilding legacy hardware into a stable learning platform using modern deployment workflows.

---

## **Technical Implementation**

### **Boot Media Preparation**

- Downloaded the official Kali ISO.
- Created a bootable USB installer using **balenaEtcher**.
- Verified USB integrity and boot compatibility on Apple hardware.
- Resolved boot selection and firmware startup issues during initial attempts.

### **System Reset & Baseline Setup**

- Booted into recovery utilities.
- Fully erased the internal storage to remove legacy macOS data.
- Repartitioned disk for Linux-only deployment.
- Established a clean installation baseline.

### **Operating System Deployment**

- Installed Kali Linux using the prepared boot media.
- Configured user accounts and hostname.
- Applied initial updates and security patches.
- Installed baseline administration tools.


---

## **Environment**

**Hardware**

- [[INTELUX-RED-01 — Apple MacBook Pro (2012)]]

**Boot Media**

- Kali Linux USB (balenaEtcher)

**Operating System**

- [[Kali Linux]]

**Role**

- Linux administration and security practice workstation

---

## **Walkthrough**

Legacy systems often accumulate configuration drift and undocumented changes over time, which makes troubleshooting difficult. To eliminate this, I rebuilt the MacBook Pro from scratch using a verified Kali installer.

I began by downloading the Kali Linux ISO and flashing it to a USB drive with balenaEtcher. This ensured a consistent and bootable installer without manual partitioning errors.

After validating the USB, I erased the internal drive to establish a known-good baseline. Removing all prior macOS partitions prevented conflicts with EFI boot records and legacy filesystem structures.

Once Kali was installed, I configured networking, user permissions, and system identity. I verified system stability using interface checks (`ip a`), hostname validation, and update testing.

This created a controlled, repeatable environment suitable for Linux administration exercises, scripting practice, pen testing, and security labs.

---

## **Validation**

- Confirmed successful boot into Kali.
- Verified network connectivity and IP assignment.
- Validated hostname and shell identity.
- Confirmed disk layout and available storage.
- Applied system updates without errors.

## **Evidence**

- Terminal output showing system identity
- Kali “About” screen
- Network interface configuration
- Disk layout verification
---

## **Lessons Learned**

- Clean baselines simplify long-term troubleshooting.
- USB imaging tools reduce deployment errors.
- Full disk wipes prevent bootloader conflicts.
- Post-install validation is critical before lab use.
- Legacy hardware remains valuable with proper rebuilds.

---

## **Outcome**

Successfully transformed aging hardware into a reliable Linux lab system. The machine now serves as a stable platform for:

- Command-line administration
- Security tooling practice
- Network testing
- Virtualization experiments
- Incident response simulations

This system is now integrated into my broader cybersecurity lab environment.