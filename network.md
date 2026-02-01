## Assumptions

The project scenario does not specify all technical and operational details required to design a complete and realistic network. The following assumptions have therefore been made to support the proposed network design. These assumptions are reasonable, limited in scope, and directly influence the design decisions presented in this report.

1. **Headquarters location**  
   The Truelec headquarters is assumed to be located in **Melbourne, Australia**. This assumption aligns with the scenario instruction for students studying at the Melbourne campus and provides a realistic basis for WAN connectivity and cloud region selection.

2. **Branch office locations**  
   Truelec is assumed to operate branch offices in the following Australian cities:  
   - **Brisbane**  
   - **Perth**  
   - **Adelaide**  
   - **Hobart**  

   While the organisation has multiple branch offices, the detailed network design is presented for **one representative branch office**, with the same design principles assumed to be applicable to the remaining branches.

3. **Number of staff at headquarters**  
   The headquarters is assumed to employ **65 staff members**, including management, project consultants, marketing personnel, and ICT staff. This number falls within the range specified in the scenario and is used to determine network capacity, WiFi coverage requirements, and equipment selection.

4. **Number of staff at branch office**  
   The designed branch office is assumed to have **20 staff members**, including electricians, engineers, site supervisors, and support staff. This assumption reflects a mid-sized branch office and informs the sizing of network infrastructure, WiFi access points, and IP address allocation.

These assumptions are used consistently throughout the network design, including the topology, IP addressing scheme, WiFi configuration, equipment selection, and capacity planning. Any variation in these assumptions would require proportional adjustments to the proposed design rather than a fundamental redesign.

## IP Addressing Plan

A structured IPv4 addressing scheme has been designed to support the headquarters and branch office networks while ensuring clarity, scalability, and ease of management. The addressing plan strictly follows the project requirements by using only `/16` and `/24` subnet masks and by basing the first octet of all IP addresses on the last two digits of the group members’ student IDs.

The addressing scheme separates major network functions into distinct sub-networks to improve manageability, reduce broadcast traffic, and support future growth.

---

### IP Addressing Design Principles

The following principles guided the IP addressing design:

- Only `/16` and `/24` subnet masks are used, as required by the project specification.
- The first octet of each IP address is derived from the student ID digits **87** and **37**.
- No private IP address ranges (e.g. 192.168.x.x or 10.x.x.x) are used.
- Separate address blocks are allocated for different functional areas such as staff, servers, WiFi, and IoT devices.
- Sufficient spare address space is reserved to accommodate organisational growth.

---

### Headquarters IP Address Allocation

The headquarters network uses the **87.0.0.0/16** address block, providing a large and flexible address space suitable for a central office with multiple services and device categories.

| Network Segment | Purpose | Address Range | Subnet Mask | Approx. Capacity | Notes |
|-----------------|---------|---------------|-------------|------------------|-------|
| HQ Staff LAN | Wired user devices for management and staff | 87.1.0.0 – 87.1.0.255 | /24 | 254 hosts | Supports current staff and moderate growth |
| HQ Server Network | Application, database, and internal service servers | 87.2.0.0 – 87.2.0.255 | /24 | 254 hosts | Isolated to improve security and performance |
| HQ WiFi Network | Wireless access for staff and authorised devices | 87.3.0.0 – 87.3.0.255 | /24 | 254 hosts | Allows for multiple devices per user |
| HQ IoT and CCTV Network | CCTV cameras, IoT sensors, RFID access systems | 87.4.0.0 – 87.4.0.255 | /24 | 254 hosts | Separated to reduce risk to core systems |
| Reserved HQ Address Space | Future expansion | 87.5.0.0 – 87.255.255.255 | /16 | Large | Reserved for additional services or growth |

---

### Branch Office IP Address Allocation

The branch office network uses the **37.0.0.0/16** address block. A simpler structure is applied due to the smaller size of branch offices while still maintaining functional separation.

| Network Segment | Purpose | Address Range | Subnet Mask | Approx. Capacity | Notes |
|-----------------|---------|---------------|-------------|------------------|-------|
| Branch Staff LAN | Wired user devices at the branch | 37.1.0.0 – 37.1.0.255 | /24 | 254 hosts | Adequate for a 20-staff branch with growth |
| Branch WiFi Network | Wireless access for branch staff | 37.2.0.0 – 37.2.0.255 | /24 | 254 hosts | Supports mobile and field devices |
| Branch IoT and CCTV Network | CCTV and access control devices | 37.3.0.0 – 37.3.0.255 | /24 | 254 hosts | Isolated to improve security |
| Reserved Branch Address Space | Future expansion | 37.4.0.0 – 37.255.255.255 | /16 | Large | Reserved for additional branches or services |

---

### IP Addressing Justification

The use of separate `/24` sub-networks for staff, servers, WiFi, and IoT devices improves logical separation and simplifies network management. This structure reduces unnecessary broadcast traffic and limits the potential impact of security incidents affecting non-critical devices such as IoT sensors or CCTV cameras.

Allocating `/16` address blocks at the site level (headquarters and branches) provides sufficient flexibility to introduce additional sub-networks in the future without requiring a complete redesign of the addressing scheme. The consistent structure across sites also simplifies troubleshooting and administration for the ICT team.

Overall, this IP addressing plan is clear, scalable, compliant with project constraints, and well suited to the operational requirements of Truelec.

## WiFi Network Design

A dedicated enterprise-grade WiFi network is designed for the Truelec headquarters to provide reliable, secure, and high-performance wireless connectivity for staff and authorised devices. The design considers the number of users, device density, coverage requirements, and security needs of a medium-sized corporate office.

---

### Access Point Deployment

Based on the assumption of approximately **65 staff members** at the headquarters and the likelihood that each staff member uses multiple wireless devices (e.g. laptop and mobile phone), the WiFi network is designed to support a high client density.

- **Number of access points:** 4
- **Placement strategy:**  
  Access points are evenly distributed across the office floor to provide overlapping coverage and minimise dead zones. Placement avoids physical obstructions such as walls and equipment rooms, and ensures coverage in meeting rooms and shared workspaces.

This deployment allows each access point to support approximately 15–20 concurrent devices, providing sufficient capacity and redundancy.

---

### Wireless Standards and Frequency Bands

- **WiFi standard:** IEEE 802.11ax (WiFi 6)  
  This standard is selected due to its improved efficiency, higher throughput, and better performance in environments with many simultaneous users compared to earlier standards.

- **Frequency bands:**  
  - **5 GHz band** is used as the primary band to provide higher throughput and reduced interference.  
  - **2.4 GHz band** is enabled for legacy device compatibility and extended coverage where required.

---

### Channel Configuration

- **5 GHz channels:**  
  Non-overlapping channels are assigned to adjacent access points to minimise co-channel interference. Automatic channel selection is enabled to allow the system to adapt to environmental changes.

- **2.4 GHz channels:**  
  Channels **1, 6, and 11** are used to avoid overlap and reduce interference.

Channel planning ensures stable performance and efficient spectrum utilisation across the office.

---

### WiFi Security Configuration

To protect organisational data and prevent unauthorised access, the following security measures are implemented:

- **Authentication and encryption:**  
  - **WPA3-Enterprise** is used for the primary staff WiFi network, providing strong encryption and centralised authentication.
  - Authentication is integrated with the organisation’s directory service to ensure only authorised users can connect.

- **Network segregation:**  
  Wireless clients are assigned to the dedicated HQ WiFi IP subnet, keeping wireless traffic logically separated from critical server and IoT networks.

- **Access control:**  
  Role-based access policies are applied to restrict access to sensitive internal resources when connected via WiFi.

---

### WiFi Design Justification

The proposed WiFi design provides a balance between performance, coverage, and security. The use of multiple access points ensures consistent coverage and supports high device density, while the selection of WiFi 6 improves efficiency in a busy office environment.

Separating the WiFi network from other network segments reduces the impact of potential security incidents and simplifies management. Overall, the design meets the operational requirements of the headquarters and aligns with industry best practices for enterprise wireless networks.

## Recommended Network Equipment

The following network equipment is recommended to support the proposed network design for the Truelec headquarters and branch office. The equipment has been selected based on performance, scalability, reliability, and suitability for a medium-sized enterprise environment. All specifications and prices are indicative and sourced from vendor or authorised reseller websites in Australian dollars (AUD).

---

### Network Equipment List

| Device Type | Manufacturer | Model | Key Specifications | Quantity | Approx. Cost (AUD) | Reference Link |
|------------|--------------|-------|--------------------|----------|--------------------|----------------|
| Edge Router | Cisco | ISR 4331 | 3× Gigabit Ethernet, WAN support, enterprise security features | 2 | $3,200 each | https://www.cisco.com |
| Core Switch | Cisco | Catalyst 2960-X | 48× Gigabit Ethernet ports, Layer 2 switching, PoE support | 1 | $4,000 | https://www.cisco.com |
| Access Switch | Cisco | Catalyst 2960-L | 24× Gigabit Ethernet ports, VLAN support, energy efficient | 2 | $2,200 each | https://www.cisco.com |
| Wireless Access Point | Cisco | Aironet 1832i | 802.11ax, dual-band (2.4/5 GHz), PoE powered | 4 | $1,200 each | https://www.cisco.com |
| Application Server | Dell | PowerEdge T350 | Intel Xeon CPU, 32 GB RAM, RAID storage, dual NICs | 3 | $3,500 each | https://www.dell.com |
| Branch Router | Cisco | ISR 4321 | 2× Gigabit Ethernet, WAN connectivity, VPN support | 1 | $2,500 | https://www.cisco.com |

---

### Equipment Selection Justification

Enterprise-grade Cisco routers and switches are selected to provide reliable WAN connectivity, robust performance, and advanced security features suitable for a multi-branch organisation. The use of dual edge routers at the headquarters improves availability by allowing continued operation in the event of a device failure.

The Cisco Catalyst switch series is chosen due to its proven reliability, support for high-speed Ethernet, and scalability. Separating core and access switching roles simplifies network management and allows the infrastructure to grow as additional users or services are introduced.

Cisco Aironet wireless access points supporting the IEEE 802.11ax standard are deployed to deliver high-performance WiFi connectivity in a high-density office environment. Power over Ethernet (PoE) support simplifies installation and reduces cabling complexity.

Dell PowerEdge servers are recommended for on-premise application hosting due to their enterprise reliability, hardware redundancy options, and suitability for continuous operation. Multiple servers are used to support the organisation’s internal systems and to improve service availability.

Overall, the selected equipment provides a balanced solution that meets current operational requirements while allowing future expansion, consistent with industry best practices for enterprise network design.
