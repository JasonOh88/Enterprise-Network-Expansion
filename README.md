# Enterprise-Network-Expansion

📖 Project Overview
This project serves as a continuation of my initial Multi-Site-Enterprise-Network deployment. As I learn the ropes of network infrastructure and work towards my CCNA, I use this space to document my routing configurations and subnetting projects.

This specific lab simulates a headquarters expanding to two new remote branch offices, focusing on efficient IP allocation, manual routing, and centralized services.

🚀 Key Technologies & Concepts Demonstrated
Variable Length Subnet Masking (VLSM): Designed an optimal addressing scheme for a /24 block across three LANs and two Point-to-Point WAN links to minimize IP waste.

Static Routing: Configured deterministic path control using specific static routes at the HQ and default static routes at the branch offices.

Centralized DNS Resolution: Deployed a DNS server to translate hostnames (e.g., intranet.technova.local) into IP addresses for seamless network navigation.

Backup & Disaster Recovery: Established a standard operating procedure (SOP) by utilizing a central TFTP server to backup running configurations from all network routers.

## 🗺️ Network Topology

<img width="1813" height="680" alt="Screenshot 2026-06-02 035016" src="https://github.com/user-attachments/assets/51af9412-3866-4cc4-92a5-2471a262c538" />

⚙️ Lab Environment & Configuration Details
To make this project highly accessible and open-source friendly, device hardening (console/SSH passwords) has been intentionally omitted. Anyone can download the .pkt file and immediately access the CLI to explore the routing tables and configurations without needing login credentials.

IP Addressing Scheme (Major Network: 192.168.10.0/24)
| Segment | Subnet (CIDR) | Usable Range |
| :--- | :--- | :--- |
| HQ LAN | 192.168.10.0 /26 | .1 - .62 |
| Branch 1 LAN | 192.168.10.64 /27 | .65 - .94 |
| Branch 2 LAN | 192.168.10.96 /28 | .97 - .110 |
| HQ-B1 WAN | 192.168.10.112 /30 | .113 - .114 |
| HQ-B2 WAN | 192.168.10.116 /30 | .117 - .118 |

Centralized HQ Services (192.168.10.2)
All major services for this lab are consolidated on a single HQ server for efficiency:

DNS Server: Translates network hostnames.

TFTP Server: Stores router configuration backups (HQ_Router_Backup, etc.).

Web Server: Hosts the internal testing page.

Configured DNS A-Records:

hq-router.technova.local ➔ 192.168.10.1

intranet.technova.local ➔ 192.168.10.2

tftp.technova.local ➔ 192.168.10.2

## ✅ Verification & Testing
The following tests were successfully conducted to validate the network:

**End-to-End Connectivity (Branch 1 to Branch 2):**

<img width="875" height="451" alt="Screenshot 2026-06-02 042119" src="https://github.com/user-attachments/assets/fdf8de64-cb95-40dc-a61e-03dd40e34eba" />

<img width="919" height="464" alt="Screenshot 2026-06-02 042146" src="https://github.com/user-attachments/assets/03a49d0a-e8c5-409d-8bf1-46c805f1c375" />


**Centralized DNS Resolution:**

<img width="692" height="293" alt="Screenshot 2026-06-02 042323" src="https://github.com/user-attachments/assets/59c0a9cd-cfd7-4e31-aa71-fccf9eadea79" />

**TFTP Configuration Backup:**

<img width="742" height="161" alt="Screenshot 2026-06-02 042506" src="https://github.com/user-attachments/assets/f7859b9c-78a8-47ff-93c3-3cbb8b1aa22b" />

<img width="656" height="124" alt="Screenshot 2026-06-02 042528" src="https://github.com/user-attachments/assets/43032dbf-610e-4d7a-9877-2d5a2f4b2ec7" />
