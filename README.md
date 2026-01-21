# Inter-Protocol-Routing-with-OSPF-RIP-EIGRP-PNETLab
This project demonstrates an inter-protocol routing design implemented in PNETLab, focusing on seamless communication between multiple routing protocols. OSPF is used as the core routing protocol with a multi-area hierarchical structure, while RIPv2 and EIGRP (AS 100) are integrated at the network edges.

Sajjad-Qasemi Project – Inter-Protocol Routing (PNETLab)
📌 Project Overview

This project is a comprehensive inter-protocol routing lab designed and implemented in PNETLab. It demonstrates how multiple routing protocols interact, redistribute routes, and maintain end-to-end connectivity across a complex enterprise-scale network.

The lab focuses on OSPF as the core protocol, while integrating RIPv2 and EIGRP (AS 100) at the edge. Route redistribution is carefully configured to ensure full reachability between all areas and protocols.

🧠 Network Design Summary
Core Protocol

OSPF (Open Shortest Path First)

Multi-area hierarchical design

Backbone: Area 0

Integrated Protocols

RIPv2 (Left side – legacy network)

EIGRP AS 100 (Right side – enterprise edge)

Routing Strategy

OSPF is used as the central routing domain

RIPv2 and EIGRP are connected to OSPF via redistribution routers (ASBRs)

🗺️ OSPF Area Structure
Area	Description
Area 0	Backbone area – main transit core
Area 10	OSPF standard area (right upper)
Area 11	OSPF standard area (right lower)
Area 20	OSPF standard area (left upper)
Area 22	OSPF standard area (left lower)
Area 100	OSPF loopback / summary area
Area 200	OSPF loopback / summary area
🔁 Inter-Protocol Connectivity
1️⃣ OSPF ↔ RIPv2 Redistribution

Location: Left side of the topology

Method:

RIPv2 runs inside a local legacy network

An ASBR router connects RIPv2 to OSPF

Routes are redistributed in both directions

Key Points:

redistribute rip subnets into OSPF

redistribute ospf 1 metric into RIP

Loopback interfaces used for router identification

Result: ✔ RIPv2 networks can reach all OSPF areas ✔ OSPF networks can reach RIPv2 endpoints

2️⃣ OSPF ↔ EIGRP (AS 100) Redistribution

Location: Right side of the topology

Method:

EIGRP AS 100 operates in an enterprise segment

Connected to OSPF via an ASBR router

Mutual redistribution is configured

Key Points:

redistribute eigrp 100 subnets into OSPF

redistribute ospf 1 metric 10000 100 255 1 1500 into EIGRP

Proper metric translation applied

Result: ✔ EIGRP networks have full access to OSPF and RIP areas ✔ OSPF core remains stable and loop-free

🔐 Loopback & Addressing Policy

All routers:

Loopback interfaces used as Route![OSPF project](https://github.com/user-attachments/assets/8e4f92ca-be3b-4029-8436-37e1976b0c11)
r-ID

Format: X.X.X.X/32

PC Interfaces:

Addressing format: X.X.X.100

Point-to-point links:

/24 subnets for clarity and learning purposes

⚙️ Key Configuration Concepts

Multi-area OSPF design (scalability & performance)

Route redistribution with controlled metrics

Prevention of routing loops

Clear separation of protocol domains

Enterprise-style hierarchical topology

🧪 Verification & Testing

Commands used for verification:

show ip route

show ip ospf neighbor

show ip eigrp neighbors

show ip protocols

ping and traceroute between different protocol domains

✔ End-to-end connectivity verified between all PCs and loopbacks

🎯 Learning Outcomes

Understanding OSPF multi-area architecture

Practical inter-protocol redistribution (OSPF, RIP, EIGRP)

Real-world enterprise routing design

Troubleshooting and verification skills

PNETLab professional topology documentation

📂 Repository Usage (GitHub Ready)

This documentation can be used directly as:

README.md for GitHub

Network design report

Lab assignment submission

Training or teaching material

👤 Author

Sajjad Qasemi
Network & IT Specialist
PNETLab | Routing Protocols | Enterprise Networking
