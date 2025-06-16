# Full-Stack Network Security Solution for a Self-Hosted Hostel Environment

## Project Overview

This project showcases the design, deployment, and management of a comprehensive, full-stack network and security solution for a new co-living hostel I did in my solo IT practice. The primary objective was to build a robust, secure, and cost-effective infrastructure from the ground up, tailored to the specific needs of a hospitality environment. This included ensuring guest privacy, providing reliable high-speed internet, and integrating value-added services like VoIP and a self-hosted media server. 

> The entire system was built around the Ubiquiti UniFi ecosystem, chosen for its powerful features, centralized management, and subscription-free model, making it an ideal long-term investment.

## Process & Methodology

The project was executed in several distinct phases, from initial consultation to final deployment and security hardening.

1. <b>Consultation & Planning</b>

- Initial Needs Assessment: The project began with in-depth discussions with the property owners to define the budget, operational requirements, and desired features. A key constraint was the budget, influenced by recent property renovations.

- Site Survey & Proposal: I conducted a thorough walkthrough and mapping of the physical space. Based on this, I created a detailed slide presentation and graphical mockups illustrating the proposed UniFi network topology, equipment placement, and the long-term cost benefits compared to subscription-based competitors.

- Cost-Effective Procurement: To align with the budget, I sourced a combination of new and reliable used equipment. This involved negotiating prices for high-quality used access points that met the performance demands of the project. I also meticulously planned and purchased all necessary materials, including cabling and raceways, to ensure a clean and safe installation, avoiding the need to break into walls.

2. <b>Physical Installation & Core Setup</b>

- Hardware Deployment: The heart of the network is a UniFi Dream Machine Special Edition (UDM-SE). This powerful device serves as the gateway, firewall, and controller for the entire UniFi ecosystem, including the Protect (camera), Network, and Talk (VoIP) applications.
  - To ensure uptime and protect against power fluctuations, the core equipment is connected to a 950W power backup (RPS).

- Structured Cabling: With the high-voltage electrical work already completed, I ran network cables neatly through the ceiling and concealed them with cable raceways. The UDM-SE was strategically placed in an office corner, with recommendations provided for a future upgrade to a dedicated server rack to optimize cooling and maintenance.

- ISP Integration: The ISP's modem did not allow for a direct fiber connection. To gain full control over traffic shaping and security, I configured the ISP's router to IP Passthrough mode, allowing the UDM-SE to act as the primary edge device for the network.

<p align="center">
<img src="https://github.com/user-attachments/assets/329aee79-4b0e-4e66-b3a9-497b9d2b36ed" width="800" height="700">

<p align="center">
<img src="https://github.com/user-attachments/assets/17e97acb-c666-432a-a1f2-c05b74554272" width="800" height="500">

<p align="center">
<img src="https://github.com/user-attachments/assets/441806d7-e6ef-49e3-b3a2-758165729d98" width="800" height="700">

3. <b>Network Configuration & Security Hardening</b>

- VLAN Segmentation: To enhance security and manage traffic, the network was segmented into three distinct VLANs:
  - Guest VLAN: For all resident and visitor devices, with client isolation enabled to prevent devices from communicating with each other.
  - Management VLAN: For core network infrastructure and administrative access.
  - Security VLAN: An isolated network exclusively for the UniFi Protect security cameras.

- Wireless Deployment: Three strategically placed UniFi Access Points (APs) were deployed to provide seamless Wi-Fi coverage across the entire property, minimizing interference and channel conflicts.

- Quality of Service (QoS): QoS rules were implemented to prioritize bandwidth for office and management tasks during peak hours while ensuring guests still had a smooth and reliable internet experience without significant downtime.

- Firewall & Threat Management:
  - The UDM-SE's built-in Intrusion Detection/Prevention System (IDS/IPS) was enabled to monitor and block malicious traffic, with a throughput capacity of up to 3.5 Gbps.
  - Firewall rules were configured to block all inbound and outbound traffic from the top 5 countries known for high rates of malicious cyber activity.
  - Custom alerts were set up to notify administrators of any suspicious activity. A recurring alert has been the detection of outbound traffic to Chinese servers triggered by TikTok Shop's embedded web ads, which the system successfully monitors.

4. <b>Value-Added Service Integration</b>

- UniFi Protect Camera System: A total of four security cameras were deployed: two indoor cameras and two outdoor, solar-powered cameras for locations where running cable was not feasible. The UDM-SE's built-in 128GB SSD, I installed a 4TB Surveillance Internal Hard Drive, and 180W PoE+ output powers the cameras and provides storage for security footage.

- UniFi Talk VoIP System: A UniFi VoIP G2 Touch phone was installed and registered in the main office. Staff were trained on its use, including call parking, transfers, and conference merging.

- Self-Hosted Media Server (Jellyfin): To provide an affordable streaming alternative, I deployed a self-hosted Jellyfin media server.

- Hardware: A modified Dell OptiPlex 7060 with an Intel i7 8th Gen processor, 64GB of RAM, and 4TB SSD of storage.

- Software: The server runs on Proxmox, a virtualized environment, hosting the open-source Jellyfin media platform through a windows machine. This allows owners and guests to stream a curated library of movies and TV shows to the main community TV and personal devices.

- Secure Remote Access: To enable secure access from outside the hostel, the Jellyfin server was exposed to the internet via Cloudflare Tunnel. Using a custom domain, I created a secure bridge with PowerShell commands in a VM, ensuring the server's IP address is never exposed directly. Automation scripts were configured to re-establish the tunnel and start all services automatically on system reboot, minimizing downtime.

## Outcome

The result was a secure, high-performance, and feature-rich network that meets all the client's initial requirements while remaining within a tight budget. The UniFi ecosystem provides a single pane of glass for managing the entire network, security, and communication infrastructure. The 2 Gbps internet connection remains stable and performant, even with active threat management and multiple services running. This project served as a practical application of network design, cybersecurity principles, and system administration skills, delivering a powerful and scalable solution for the client.
