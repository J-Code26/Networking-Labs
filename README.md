# Network Engineering & Infrastructure Security Labs

This repository documents hands-on network architecture, infrastructure engineering, and defensive network security implementations. It tracks technical progression through Cisco CCNA-aligned environments, practical hardening frameworks, and simulated attack-defense scenarios across simulated and physical lab hardware.

---

## Technical Focus Areas

- **Hardening & Device Security:** Secure device access (SSH, AAA, RADIUS/TACACS+), disabling insecure services, password encryption, and management plane protection.
- **Layer 2 Security:** Port Security, DHCP Snooping, Dynamic ARP Inspection (DAI), IP Source Guard, and VLAN segmentation/isolation (Private VLANs).
- **Traffic Filtering & Threat Control:** Standard and Extended Access Control Lists (ACLs), reflexive/stateful filtering, and edge traffic mitigation.
- **Perimeter & Remote Access Defense:** Site-to-site IPsec VPNs, remote access VPNs, zone-based policy firewalls (ZBF), and NAT/PAT inspection.
- **Monitoring & Defensive Forensics:** SNMPv3 monitoring, Syslog logging, NetFlow/traffic flow inspection, and packet capture analysis.

---

## Goals

- Implement and audit core network infrastructure through a security-first lens.
- Reinforce CCNA Security and enterprise networking domains with reproducible lab configurations.
- Design attack-and-mitigation workflows (e.g., simulating ARP spoofing or unauthorized DHCP, then applying Layer 2 defenses).
- Develop structured engineering documentation, configuration scripts, and post-incident verification logs.
- Build an audit-ready technical portfolio showcasing end-to-end network deployment and defense.

---

## Lab Environment & Tooling

| Category | Tools & Hardware |
| :--- | :--- |
| **Simulation & Emulation** | Cisco Packet Tracer, GNS3 / EVE-NG |
| **Hardware & Endpoints** | Managed Enterprise Switch, Raspberry Pi (Bastion/Attacker host), Cat6/Cat6e Cabling |
| **Analysis & Auditing** | Wireshark, CLI inspection commands (`show ip dhcp snooping binding`, `show mac address-table`), Nmap/ping sweeps |
| **Protocols & Concepts** | 802.1Q VLANs, OSPF, STP/RSTP (BPDU Guard, Root Guard), DHCP Snooping, DAI, IPsec, ACLs |
| **Version Control** | Git, GitHub, Markdown Documentation |

---

## Engineering Workflow

1. **Architecture & Threat Modeling:** Sketch the network topology, identify trust boundaries, untrusted subnets, and potential attack vectors.
2. **Topology Deployment:** Build the base infrastructure in Cisco Packet Tracer or on physical lab hardware.
3. **Baseline Configuration:** Configure addressing, routing (OSPF), trunking, and basic connectivity.
4. **Security Implementation:** Apply targeted hardening (Port Security, DAI, DHCP Snooping, ACLs, SSH/crypto keys, BPDU Guard).
5. **Adversarial Testing (Break / Audit):** Inject rogue traffic, test boundary violations, simulate unauthorized MAC addresses, or attempt misdirected routing.
6. **Verification & Forensics:** Capture verification commands (`show port-security interface`, log alerts, drops) and confirm security posture.
7. **Documentation & Release:** Commit lab topologies (`.pkt`), annotated running-configs, verification outputs, and remediation notes to GitHub.
