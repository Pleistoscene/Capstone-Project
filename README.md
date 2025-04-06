# MITT NSA630 Capstone Project – Emerald Tech

## Overview

This repository contains the complete documentation and configuration files for the NSA630 Capstone Project at MITT. The goal of this project was to design and implement a functional, secure, and redundant IT infrastructure for a small school environment.

---

## Scenario

A new small school requires a complete IT infrastructure. The solution must provide:
- Internet access
- Directory services (Active Directory)
- DNS and DHCP
- Internal email services
- Internal web hosting
- Network segmentation and VLANs
- Redundancy at Layer 2 and Layer 3
- Security hardening and access control

---

## Technologies Used

- Cisco Routers & Switches (Configured via CLI)
- Windows Server 2025 (Standard Desktop Experience)
- Proxmox VE (for server virtualization)
- Microsoft Active Directory, DNS, DHCP
- Microsoft Exchange Server (internal email)
- IIS Web Server (internal website)
- NAT via MITT Capstone subnet

---

## VLAN Design

| VLAN ID | Name        | Purpose               |
|---------|-------------|------------------------|
| 10      | Servers     | AD, DNS, DHCP, Email   |
| 20      | IT          | Admin Access           |
| 30      | Faculty     | Instructors & Staff    |
| 40      | Students    | Student PCs            |
| 50      | Classroom   | In-classroom PCs       |
| 60      | Library     | Library PCs            |
| 70      | Lab         | Computer Lab PCs       |
| 999     | Parking Lot | Default VLAN           |

---

## IP Addressing Scheme

- **Internal Network**: `192.168.100.0/24`
- **Gateway**: `192.168.100.1`
- **DC-01 (AD/DNS/DHCP)**: `192.168.100.2`
- **EX-01 (Exchange/Web)**: `192.168.100.3`
- **IT-PC**: `192.168.100.4`
- **Printers**: Reserved static IPs

---

## Project Contents

- [`Capstone_Documentation.md`](./Capstone_Documentation.md) – Detailed project breakdown
- [`network_config/`](./network_config) – Router and switch configs
- [`server_config/`](./server_config) – Windows Server configuration steps
- [`diagrams/`](./diagrams) – Logical and physical topology images
- [`policies/`](./policies) – User groups, GPOs, and ACL documentation

---

## Team

**Emerald Tech – MITT Spring 2025**
- Aaron Queskekapow – Lead Network Designer & Sysadmin
- [Other members here if needed]

---

## License

This project is part of an educational assignment and is not licensed for commercial use.

---

## Notes

Please ensure all `.txt` configs are opened with a code editor for proper formatting.
