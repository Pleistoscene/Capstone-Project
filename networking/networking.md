# Networking

**Author:** Aaron Queskekapow  
**Project:** MITT NSA630 Capstone – Final Infrastructure Design  
**Domain:** RAHJ.local  
**Version:** 1.3  
**Last Updated:** 2025-04-12  

## Overview
This document outlines the core addressing, segmentation, connectivity, redundancy, and service deployment details of the RAHJ High School network environment designed for the NSA630 Capstone Project.

## Addressing & DHCP

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
| Web Server  | S1 F0/3     | 192.168.10.12  | 255.255.255.0 | 192.168.10.254    |
| IT PC       | S1 F0/4     | 192.168.20.50  | 255.255.255.0 | 192.168.20.254    |
| OFF-PC 1    | S1 F0/5     | DHCP           | DHCP          | DHCP              |
| OFF-PC 2    | S1 F0/6     | DHCP           | DHCP          | DHCP              |
| OFF-PC 3    | S1 F0/7     | DHCP           | DHCP          | DHCP              |
| OFF-Printer | S1 F0/8     | 192.168.30.49  | 255.255.255.0 | 192.168.30.254    |
| OFF-Wifi    | S1 F0/10    | 192.168.30.48  | 255.255.255.0 | 192.168.30.254    |
| DC-02       | S2 F0/1     | 192.168.10.13  | 255.255.255.0 | 192.168.10.254    |
| STU-Wifi    | S2 F0/10    | 192.168.40.49  | 255.255.255.0 | 192.168.40.254    |
| CL-PC 1–8   | S3 F0/1-8   | DHCP           | DHCP          | DHCP              |
| LI-PC 1–6   | S3 F0/9-14  | DHCP           | DHCP          | DHCP              |
| LI-Printer  | S3 F0/15    | 192.168.60.49  | 255.255.255.0 | 192.168.60.254    |
| LAB-PC 1–20 | S4 F0/1-20  | DHCP           | DHCP          | DHCP              |
| LAB-Printer | S4 F0/21    | 192.168.70.49  | 255.255.255.0 | 192.168.70.254    |

|   VLAN | Name       | Subnet          | Gateway        | DHCP Range        | Notes                                                    |
|-------:|:-----------|:----------------|:---------------|:------------------|:---------------------------------------------------------|
|     10 | Servers    | 192.168.10.0/24 | 192.168.10.254 | Static Only       | DCs, File, Web Servers are static                        |
|     20 | IT         | 192.168.20.0/24 | 192.168.20.254 | Static Only       | Switches and IT PC are static                            |
|     30 | Staff      | 192.168.30.0/24 | 192.168.30.254 | 192.168.30.50–69  | Office PCs are DHCP, Printer, Staff Wi-Fi are static     |
|     40 | Students   | 192.168.40.0/24 | 192.168.40.254 | 192.168.40.50–129 | Wi-Fi device is static                                   |
|     50 | Classroom  | 192.168.50.0/24 | 192.168.50.254 | 192.168.50.50–57  | PCs are DHCP, none static                                |
|     60 | Library    | 192.168.60.0/24 | 192.168.60.254 | 192.168.60.50–55  | PCs are DHCP, Printer is static                          |
|     70 | Lab        | 192.168.70.0/24 | 192.168.70.254 | 192.168.70.50–69  | PCs are DHCP, Printer is static                          |
|    999 | ParkingLot | N/A             | N/A            | None              | No IPs assigned                                          |

### DHCP – Use Case and Configuration
- DHCP is used to dynamically assign IP addresses to **end-user devices** across VLANs including Staff, Students, Lab, Library, and Classroom.
- DHCP is **centrally managed on DC-01** and replicated to DC-02 for redundancy using **DHCP Failover Load Balance** mode.
- Each VLAN has a defined DHCP range, lease time, and excluded static blocks.

📷 *Screenshot:* DHCP Manager showing all scopes + PowerShell output using `Get-DhcpServerv4Scope`

### Static IPs – Use Case and Configuration
- Devices like domain controllers (DC-01, DC-02), file server (FS-01), web server, switches (S1–S4), and printers are configured with static IPs.
- Gateways (.254), DHCP exclusions (.1–.49), and DNS servers (.10, .13) follow structured static planning.

## End-to-End Connectivity

### Internet Reachability
- R1 and R2 connect to the external **Capstone NAT gateway** using public subnet **10.128.250.0/24**.
- NAT with HSRP (Hot Standby Router Protocol) ensures automatic failover of outbound internet access.
- Domain-joined clients and the web server can access external domains.

📷 *Screenshot:* Web browser open on a lab PC reaching www.google.com

### Host-to-Host Reachability
- Devices across all VLANs can reach each other as intended, except where restricted by ACLs.
- Testing included ICMP, SMB, RDP, and domain join operations.

📷 *Screenshot:* Ping test from IT PC to Lab, Library, and Server VLANs

## Segmentation & Security

### VLAN Implementation
|   VLAN | Name       | Interface Assigned               | Purpose                            |
|-------:|:-----------|:---------------------------------|------------------------------------|
|     10 | Servers    | S1: F0/1-3                       | AD, DNS, DHCP, Fileshare, Backups  |
|     20 | IT         | S1: F0/4                         | IT/Admin Access                    |
|     30 | Staff      | S1: F0/5-10                      | Office PCs/Printer/Staff-Wifi      |
|     40 | Students   | S2: F0/10                        | Student Wifi                       |
|     50 | Classroom  | S3: F0/1-8                       | In-classroom PCs                   |
|     60 | Library    | S3: F0/9-15                      | Library PCs/Printer                |
|     70 | Lab        | S4: F0/1-21                      | Computer Lab PCs/Printer           |
|    999 | ParkingLot | Trunk ports (inter-switch links) | Default VLAN                       |

- VLANs 10–70 represent logical groupings (Servers, IT, Staff, Students, etc.). VLAN 999 used for ParkingLot/default trunk.
- All switches are configured with proper VLAN membership and access/trunk modes.

📷 *Screenshot:* `show vlan brief` output from S1

### Subnetting
|   VLAN | Name       | Subnet          |
|-------:|:-----------|:----------------|
|     10 | Servers    | 192.168.10.0/24 |
|     20 | IT         | 192.168.20.0/24 |
|     30 | Staff      | 192.168.30.0/24 |
|     40 | Students   | 192.168.40.0/24 |
|     50 | Classroom  | 192.168.50.0/24 |
|     60 | Library    | 192.168.60.0/24 |
|     70 | Lab        | 192.168.70.0/24 |
|    999 | ParkingLot | N/A             |

- Each VLAN is subnetted within the **192.168.0.0/16** private space.
- Subnetting aligns 1:1 with VLANs using /24 masks (e.g., 192.168.10.0/24 → VLAN 10)

### ACLs
ACLs are used to segment traffic, ensuring only authorized services are reachable while allowing general internet access.

#### ACL_STUDENT_INTERNET_ONLY
**Purpose:** Restrict Student VLAN (VLAN 40) to internal services only (DNS, DHCP, Web) and allow full internet access.

- Allow DNS (UDP/TCP port 53) to internal and external DNS
- Allow DHCP replies from DC-01 and DC-02
- Allow HTTP/HTTPS to internal web server (192.168.10.12)
- Deny all internal VLAN access (10–70)
- Permit all remaining traffic (Internet)

**Applied to:** `GigabitEthernet0/0/0.40` (VLAN 40 - Students)

#### ACL_LIMITED_DC_IT
**Purpose:** Permit core AD services for domain communication and block other internal access.

- Allow DNS, DHCP, Kerberos, LDAP, Netlogon, RPC, SMB
- Allow HTTP/HTTPS to internal web server
- Deny general access to VLANs 10 and 20
- Permit all remaining traffic (e.g., internet)

 **Applied to:**
- `GigabitEthernet0/0/0.30` (VLAN 30 - Staff)
- `GigabitEthernet0/0/0.50` (VLAN 50 - Classroom)
- `GigabitEthernet0/0/0.60` (VLAN 60 - Library)
- `GigabitEthernet0/0/0.70` (VLAN 70 - Lab)

📷 *Screenshot:* `show access-lists` or running-config from router with `ip access-list` section

## 🔁 Redundancy

### EtherChannel

| Port Channel | Switches         | Interfaces Used     | Description                      |
|--------------|------------------|----------------------|---------------------------------|
| Po1          | S1 ↔ S3          | F0/23, F0/24         | Trunk link carrying VLANs 10–70 |
| Po1          | S2 ↔ S4          | F0/23, F0/24         | Trunk link carrying VLANs 10–70 |

EtherChannel is used to increase bandwidth and provide redundancy between switches. The following port channels were configured:

- EtherChannel configured between:
  - S1 ↔ S3 using Po1 on F0/23–F0/24
  - S2 ↔ S4 using Po1 on F0/23–F0/24
- Trunk links carry VLANs 10–70 with LACP (`channel-group 1 mode active`)

📷 *Screenshot:* `show etherchannel summary` on S1 and S2

### FHRP – HSRP
- R1 and R2 use **HSRP** on G0/0/0 subinterfaces
- Virtual IPs (`.254`) used as default gateway for each VLAN
- Priority and preemption ensure failover to R2 if R1 goes down

📷 *Screenshot:* `show standby brief` from R1 and R2

### Dynamic Routing
- **RIPv2** has been enabled on both R1 and R2 to allow automatic advertisement of all internal VLAN subnets.
- This supports future scalability by removing the need for manually defining static routes as new VLANs or subnets are added.
- Configuration applied to both routers:

```plaintext
router rip
 version 2
 no auto-summary
 network 192.168.0.0
```

📷 *Screenshot:* `show ip protocols` or `show ip route rip` output from R1 and R2 showing learned routes

## Summary

| Category             | Description                                 |
|----------------------|---------------------------------------------|
| **DHCP**             | Centralized DHCP with proper VLAN scopes    |
| **Static IP**        | Used for infrastructure devices & servers   |
| **Internet Access**  | NAT via HSRP-enabled routers to Capstone    |
| **Host Reachability**| Full intra/inter-VLAN reachability          |
| **VLAN**             | Proper design and interface assignment      |
| **Subnet**           | One-to-one with VLANs, /24 masks            |
| **ACLs**             | Segmentation rules applied per VLAN         |
| **EtherChannel**     | Configured with LACP for redundancy         |
| **FHRP (HSRP)**      | R1/R2 virtual gateway failover setup        |
| **Dynamic Routing**  | RIPv2 enabled on both routers               |


- All EtherChannels are configured in **trunk mode** using **LACP**
- VLANs 10 through 70 are allowed across all trunks
- EtherChannels provide higher throughput and link redundancy

