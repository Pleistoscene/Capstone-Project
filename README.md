# MITT NSA630 Capstone Project

## Overview

This repository contains the complete documentation and configuration files for the NSA630 Capstone Project at MITT. The goal of this project was to design and implement a functional, secure, and redundant IT infrastructure for a small school environment.

---

## Scenario

A new small school requires a complete IT infrastructure. The solution must provide:
- Internet access
- Directory services (Active Directory)
- DNS and DHCP
- Email services
- Website
- Network segmentation and VLANs
- Redundancy at Layer 2 and Layer 3
- Security hardening and access control
- Secured GPO's

---

## Technologies Used

- Cisco Routers & Switches (Configured via CLI)
- Windows Server 2025 (Standard Desktop Experience)
- Ubuntu 24.04 LTS
- 2 School PC Towers (DC-01 && FS-01)
- 1 TP-Link Wifi Router

---

## Project Contents

- [`Capstone_Documentation.md`]– Detailed project breakdown
- [`network_config/`] – Router and switch configs
- [`server_config/`]– Windows Server configuration steps
- [`diagrams/`] – Logical and physical topology images
- [`policies/`]– User groups, GPOs, and ACL documentation

---

## Team

- Aaron Queskekapow – Lead Network Designer & Sysadmin

---

## License

This project is part of an educational assignment and is not licensed for commercial use.

---

## Network Addressing Tables

| Device      | Interface   | IP Address     | Subnet Mask   | Default Gateway   |
|:------------|:------------|:---------------|:--------------|:------------------|
| R1          | G0/0/0      | N/A            | N/A           | N/A               |
| R1          | G0/0/0.10   | 192.168.10.1   | 255.255.255.0 | N/A               |
| R1          | G0/0/0.20   | 192.168.20.1   | 255.255.255.0 | N/A               |
| R1          | G0/0/0.30   | 192.168.30.1   | 255.255.255.0 | N/A               |
| R1          | G0/0/0.40   | 192.168.40.1   | 255.255.255.0 | N/A               |
| R1          | G0/0/0.50   | 192.168.50.1   | 255.255.255.0 | N/A               |
| R1          | G0/0/0.60   | 192.168.60.1   | 255.255.255.0 | N/A               |
| R1          | G0/0/0.70   | 192.168.70.1   | 255.255.255.0 | N/A               |
| R1          | G0/0/0.999  | N/A            | N/A           | N/A               |
| R1          | G0/0/1      | 10.128.250.120 | 255.255.255.0 | N/A               |
| R2          | G0/0/0      | N/A            | N/A           | N/A               |
| R2          | G0/0/0.10   | 192.168.10.1   | 255.255.255.0 | N/A               |
| R2          | G0/0/0.20   | 192.168.20.1   | 255.255.255.0 | N/A               |
| R2          | G0/0/0.30   | 192.168.30.1   | 255.255.255.0 | N/A               |
| R2          | G0/0/0.40   | 192.168.40.1   | 255.255.255.0 | N/A               |
| R2          | G0/0/0.50   | 192.168.50.1   | 255.255.255.0 | N/A               |
| R2          | G0/0/0.60   | 192.168.60.1   | 255.255.255.0 | N/A               |
| R2          | G0/0/0.70   | 192.168.70.1   | 255.255.255.0 | N/A               |
| R2          | G0/0/0.999  | N/A            | N/A           | N/A               |
| R1          | G0/0/1      | 10.128.250.121 | 255.255.255.0 | N/A               |
| S1          | VLAN 20     | 192.168.20.11  | 255.255.255.0 | 192.168.20.254    |
| S2          | VLAN 20     | 192.168.20.12  | 255.255.255.0 | 192.168.20.254    |
| S3          | VLAN 20     | 192.168.20.13  | 255.255.255.0 | 192.168.20.254    |
| S4          | VLAN 20     | 192.168.20.14  | 255.255.255.0 | 192.168.20.254    |
| DC-01       | S1 F0/1     | 192.168.10.10  | 255.255.255.0 | 192.168.10.254    |
| FS-01       | S1 F0/2     | 192.168.10.11  | 255.255.255.0 | 192.168.10.254    |
| Web Server  | Virtual     | 192.168.10.12  | 255.255.255.0 | 192.168.10.254    |
| IT PC       | S1 F0/3     | 192.168.20.50  | 255.255.255.0 | 192.168.20.254    |
| OFF-PC 1    | S1 F0/4     | DHCP           | DHCP          | DHCP              |
| OFF-PC 2    | S1 F0/5     | DHCP           | DHCP          | DHCP              |
| OFF-PC 3    | S1 F0/6     | DHCP           | DHCP          | DHCP              |
| OFF-Printer | S1 F0/7     | 192.168.30.49  | 255.255.255.0 | 192.168.30.254    |
| OFF-Wifi    | S1 F0/8     | 192.168.30.48  | 255.255.255.0 | 192.168.30.254    |
| STU-Wifi    | S2 F0/8     | 192.168.40.49  | 255.255.255.0 | 192.168.40.254    |
| CL-PC 1–8   | S3 F0/1-8   | DHCP           | DHCP          | DHCP              |
| LI-PC 1–6   | S3 F0/9-14  | DHCP           | DHCP          | DHCP              |
| LI-Printer  | S3 F0/15    | 192.168.60.49  | 255.255.255.0 | 192.168.60.254    |
| LAB-PC 1–20 | S4 F0/1-20  | DHCP           | DHCP          | DHCP              |
| LAB-Printer | S4 F0/21    | 192.168.70.49  | 255.255.255.0 | 192.168.70.254    |

---

## VLAN Design

|   VLAN | Name       | Interface Assigned               | Purpose                            |
|-------:|:-----------|:---------------------------------|------------------------------------|
|     10 | Servers    | S1: F0/1-3                       | AD, DNS, DHCP, Fileshare, Backups  |
|     20 | IT         | S1: F0/3                         | IT/Admin Access                    |
|     30 | Staff      | S1: F0/4-8                       | Staff                              |
|     40 | Students   | S2: F0/8                         | Student Use                        |
|     50 | Classroom  | S3: F0/1-8                       | In-classroom PCs                   |
|     60 | Library    | S3: F0/9-15                      | Library PCs                        |
|     70 | Lab        | S4: F0/1-21                      | Computer Lab PCs                   |
|    999 | ParkingLot | Trunk ports (inter-switch links) | Default VLAN                       |

---

## DHCP

|   VLAN | Name       | Subnet          | Gateway        | DHCP Range        | Notes                               |
|-------:|:-----------|:----------------|:---------------|:------------------|:------------------------------------|
|     10 | Servers    | 192.168.10.0/24 | 192.168.10.254 | Static Only       | DC, File, Web Servers are static    |
|     20 | IT         | 192.168.20.0/24 | 192.168.20.254 | Static Only       | Switches and IT PC are static       |
|     30 | Staff      | 192.168.30.0/24 | 192.168.30.254 | 192.168.30.50–59  | Printers and staff Wi-Fi are static |
|     40 | Students   | 192.168.40.0/24 | 192.168.40.254 | 192.168.40.50–129 | Wi-Fi device is static              |
|     50 | Classroom  | 192.168.50.0/24 | 192.168.50.254 | 192.168.50.50–57  | PCs in DHCP, none static            |
|     60 | Library    | 192.168.60.0/24 | 192.168.60.254 | 192.168.60.50–55  | PCs in DHCP, printer is static      |
|     70 | Lab        | 192.168.70.0/24 | 192.168.70.254 | 192.168.70.50–69  | PCs in DHCP, printer is static      |
|    999 | ParkingLot | N/A             | N/A            | None              | No IPs assigned                     |
