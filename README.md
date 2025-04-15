# NSA630 Capstone Project – RAHJ High School Infrastructure

Welcome to the official repository for the MITT NSA630 Capstone Project by Group 1. This project showcases the design, configuration, and deployment of a fully functional and secure IT infrastructure for a fictional high school, RAHJ High.

## Project Overview
This capstone project demonstrates our ability to plan, implement, and secure a real-world network for a small educational institution. Key components include:

- VLAN-based network segmentation
- Redundant routing with HSRP and NAT failover
- Windows Server 2025 with AD DS, DNS, and DHCP
- Internal web hosting (rahj.ca) using Apache on Ubuntu
- Microsoft 365 integration for email
- Network security via ACLs, port security, and hardening
- Group Policy for access control and auditing

## Technologies Used
- Cisco Routers & Switches (CLI)
- Windows Server 2025 (GUI)
- Ubuntu 24.04 LTS (Apache2 Web Server)
- Microsoft 365 (Email & DNS Integration)
- Group Policy Management (GPMC)
- GitHub for documentation
- GoDaddy DNS (rahj.ca management)
- PC Towers for Servers

## Key Features
- **Security Hardening**: Password protection, SSH-only remote access, banners, ACLs, and port security on all switches and routers
- **Redundancy**: Two routers (R1 & R2) using HSRP with NAT failover for internet-facing services
- **VLAN Segmentation**: Dedicated VLANs for Servers, IT, Staff, Students, Classrooms, Library, and Lab
- **Monitoring & Control**: GPO-based restrictions, login auditing, user policies, and centralized DNS/DHCP
- **Web & Email Services**: Secure Apache-hosted site (rahj.ca) and Microsoft 365 for domain-based email

## Repository Structure
| Folder                 | Description                                                                                      |
|------------------------|--------------------------------------------------------------------------------------------------|
| `additional/`          | Additional stuff                                                                                 |
| `configurations/`      | Cisco device configs for routers (R1, R2) and switches (S1–S4), including VLANs, HSRP, SSH, etc. |                                                               |
| `networking/`          | IP addressing schemes, DHCP scopes, subnetting plans, NAT logic, and inter-VLAN routing details  |
| `security hardening/`  | ACL configurations, port security, router/switch hardening commands, website security.           |
| `server & services/`   | Windows Server 2025 setup for AD DS, DNS, DHCP; Apache site config; Microsoft 365 & rahj.ca setup|


## Domain
- **Internal Domain**: RAHJ.local (Windows Active Directory)
- **External Domain**: rahj.ca (managed via GoDaddy DNS)
- **Email Provider**: Microsoft 365 (configured with rahj.ca)

## Group 1
- **Aaron Queskekapow** – Lead Infrastructure & Systems
- **Ravneet Kaur** - Server and Services Administrator
- **Harpreet Singh** - Active Directory and Group Policy Manager
- **Jaskirat Kaur Brar** - Presentation and Demo Coordinator

## How to Use
This repository is designed for educational demonstration purposes. Config files and documentation can be reused for labs, IT infrastructure templates, or future learning environments. Ensure appropriate modifications are made for production environments.

## License
This project is for academic use under MITT guidelines. No commercial use without written permission.

## References
- **Microsoft Docs**
  - [Active Directory-Integrated DNS Zones](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/active-directory-integrated-dns-zones)
  - [Repadmin Tool](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/cc770963(v=ws.11))
- **Ubuntu Docs**
  - [Netplan Configuration Reference](https://netplan.io/reference/)
- **Cisco Docs**
  - [Port Security Configuration Guide](https://www.cisco.com/c/en/us/support/docs/lan-switching/port-security/12062-48.html)
- **GoDaddy Help**
  - [Manage DNS Records](https://ca.godaddy.com/help/manage-dns-records-680)

### YouTube Tutorials
- NetworkChuck – [How to Build an Active Directory Lab (2023)](https://www.youtube.com/watch?v=2ToYMhBTwGg)
- David Bombal – [Configure VLANs, Trunking, and Routing on Cisco Switches](https://www.youtube.com/watch?v=bWvgvBzEA2I)
- Professor Messer – [CompTIA Network+ DNS Topics](https://www.youtube.com/watch?v=Ph0uNQEqSPc)
- Chris Titus Tech – [Set Up a DNS Server on Windows Server](https://www.youtube.com/watch?v=HnJrx8reFTg)
- Windows Ninja – [Install DHCP on Windows Server 2022/2019](https://www.youtube.com/watch?v=liSoMCfqkH4)

### Academic & Lab Resources
- **MITT MyLearning Labs** – Practical hands-on labs provided by Manitoba Institute of Trades and Technology (MITT) covering Active Directory, DNS, DHCP, GPOs, VLAN configuration, switch/router security, and server roles.
- **CCNA Coursework (v7.0)** – Cisco Networking Academy materials covering:
  - Switching, Routing, and Wireless Essentials
  - Network Security and Troubleshooting
  - Subnetting and IP Addressing
  - ACLs and NAT configuration
  - Redundancy protocols (HSRP, EtherChannel, STP)

### AI Assistance
- **ChatGPT (OpenAI)** – Provided continuous support with network design decisions, documentation writing, command syntax, troubleshooting, and general best practices throughout the Capstone project.

