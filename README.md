# NSA630 Capstone Project – RAHJ High School Infrastructure

Welcome to the official repository for the MITT NSA630 Capstone Project by Group 1. This project showcases the design, configuration, and deployment of a fully functional and secure IT infrastructure for a fictional high school, RAHJ High.

## Project Overview
This capstone project demonstrates our ability to plan, implement, and secure a real-world network for a small educational institution. Key components include:

- Network topology and VLAN segmentation
- Redundant routing with HSRP and NAT failover
- Active Directory, DNS, and DHCP on Windows Server 2025
- Group Policy Objects for centralized management
- Switch and router security hardening
- Internal Apache-based website (rahj.ca)

## 🛠 Technologies Used
- Cisco Routers & Switches (CLI-based)
- Windows Server 2025 (GUI)
- Ubuntu 24.04 LTS (Apache2 Web Server)
- Microsoft Exchange Server
- Group Policy Management Console (GPMC)
- GoDaddy DNS Management
- GitHub for documentation

## Key Features
- **Security Hardening**: ACLs, SSH-only access, banner warnings, port security, and GPO restrictions
- **Redundancy**: HSRP-enabled routers with NAT redundancy for failover
- **Segmentation**: VLANs assigned for Students, Staff, IT, Servers, Classrooms, Library, Lab, and Guest Wi-Fi
- **Monitoring**: Security auditing via GPOs and centralized logging
- **Web & Email Hosting**: SSL-enabled Apache site hosted on Ubuntu VM; Microsoft Exchange handling email under `rahj.ca`

## Domain
- **Internal**: RAHJ.local (AD DS domain)
- **External**: rahj.ca (DNS hosted by GoDaddy, points to internal website)

## Group 1
- **Aaron Queskekapow** – Lead Infrastructure & Systems
- *(other members here and their roles)*

## How to Use
This repository is designed for educational demonstration purposes. Config files and documentation can be reused for labs, IT infrastructure templates, or future learning environments. Ensure appropriate modifications are made for production environments.

## License
This project is for academic use under MITT guidelines. No commercial use without written permission.
