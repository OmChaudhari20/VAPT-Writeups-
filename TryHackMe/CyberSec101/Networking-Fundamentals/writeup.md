# Networking Fundamentals

## Overview
Foundational networking concepts covering network types, the OSI/TCP-IP models, 
cabling standards, MAC/IP addressing, ARP, and core networking devices — the 
building blocks for understanding how data moves across a network.

## History
- ARPANET (1960s) — the origin of modern computer networking

## Types of Networks
| Type | Full Form | Coverage |
|---|---|---|
| LAN | Local Area Network | Devices connected via cable within one building/office |
| MAN | Metropolitan Area Network | Covers one city to another, shares data via wireless |
| WAN | Wide Area Network | Covers one state/country to another |
| PAN | Personal Area Network | Minimal range — connects devices like phones, earphones via Bluetooth |

**Peer to Peer**: Every device has its own network with no central request/response — devices can share data directly with anyone.

## Key Networking Metrics
- **Latency**: Time taken for data to travel from one place to another
- **Bandwidth**: How much data can travel in a given time
- **Throughput**: Actual internet speed achieved
- **Jitter**: Variation/inconsistency in internet speed (like "mood swings" in connection speed)

## Client-Server Model
When a client opens a browser and sends a request for data, the request travels through the internet to the server. The server accepts the request, processes it, and delivers the requested data packets back to the client.

## OSI Model (7 Layers)
| Layer | Name | Function |
|---|---|---|
| 7 | Application | User-facing applications |
| 6 | Presentation | How data is presented to users |
| 5 | Session | Manages whether communication is established properly |
| 4 | Transport | TCP-like protocols, segmentation |
| 3 | Network | IP addressing, routing |
| 2 | Data Link | MAC addressing |
| 1 | Physical | Physical medium — LAN, cables, routers |

**Encapsulation**: The process of adding headers to data as it travels down the layers.
**Decapsulation**: The process of removing headers as data travels up the layers to be read.

## TCP/IP Model
- **Application** → Combines Presentation & Session layers
- **Transport** → Maintains packet delivery
- **Internet** → Equivalent to Network layer
- **Network Access** → Combines Physical & Data Link layers

## Cabling
- **Copper**: 1st generation, ~100MB latency
- **Fiber**: 2nd generation, ~10GB latency, broadest transmission range
- **Coaxial**: Latest version for data transmission
- **RJ45**: Standard port/connector used in LAN
- **SFP / SFP+**: Connector type used in servers
- **QSFP**: Advanced version of SFP
- Link Speed & PoE: Power over Ethernet

**Cable Standards**: Cat 5 & Cat 5e — used for small-distance connections (e.g. 1st to 2nd floor); mostly used in offices. Cat 6 — newer standard, gives better speed.

## Ethernet Frame & MAC Address
- **Destination MAC**: Receiver's MAC address
- **Source MAC**: Sender's MAC address
- **Payload**: The actual data being transmitted, referred to as "payload" because data is transmitted in encrypted form
- **TTL (Time To Live)**: Responsible for ensuring packets reach their destination correctly
- **Protocol**: Determines which protocol is used (TCP, UDP)
- **Checksum**: Error detection — ensures no errors occur during transmission

## ARP (Address Resolution Protocol)
- **ARP Request/Reply**: A device asks for data via MAC address; the target provides permission, space, and a valid IP; data is then sent to the transport layer
- **ARP Table**: Works like a phonebook — checks which MAC address corresponds to which system
- **ARP Spoofing**: An attack where a malicious actor sends fake ARP requests to steal data

## Networking Devices
- **Hub**: Connects multiple devices; broadcasts to all (not targeted)
- **Switch**: Connects multiple devices but is NOT a broadcasting device — more efficient than a hub
- **Router**: Used for transmitting data between networks; connects to other routers
- **Managed vs Unmanaged Switch**: A managed switch allows full configuration (ports, cabling, etc.); an unmanaged switch is plug-and-play with no configuration needed

## Router Basics & Packet Forwarding
- **NAT (Network Address Translation)**: Converts a private IP into a public IP
- **PAT (Port Address Translation)**: Handles port-level address translation
- **Address Translation**: Converts a larger address space into a smaller one

## Static vs Dynamic Routing
- **Static Routing**: All settings (IP address, gateway IP) are configured manually
- **Dynamic Routing**: Uses multiple protocols and software-based networking to configure across multiple systems automatically

## IPv4 vs IPv6
- **IPv4**: Each connected device is assigned a unique identifying IP address
- **IPv6**: Represented using hexadecimal numbers (e.g. `fe80:6768::1349::23bc::1fe7a`)

## IP Address Classes
| Class | Range | Subnet Mask | Usage |
|---|---|---|---|
| A | 0–127 | 255.0.0.0 | Large organizations |
| B | 128–191 | 255.255.0.0 | Medium networks |
| C | 192–223 | 255.255.255.0 | Small office/home |
| D | 224–239 | Multicast | Group messaging |
| E | 240–255 | Experimental | Labs |

## Key Takeaway
<img width="1223" height="529" alt="Screenshot 2026-07-15 222233" src="https://github.com/user-attachments/assets/fb36484d-df42-46c1-b8f6-044814be2669" />
<img width="1235" height="529" alt="Screenshot 2026-07-20 215426" src="https://github.com/user-attachments/assets/b3046f13-6e78-4f7b-bc4c-424fbfaedc40" />
<img width="1228" height="532" alt="Screenshot 2026-07-21 170825" src="https://github.com/user-attachments/assets/ae54793b-87f4-431e-97fd-ff12ce003054" />

Understanding networking fundamentals — from the OSI model to ARP and IP addressing — 
is essential groundwork for VAPT, since network-level reconnaissance and attacks 
(ARP spoofing, MITM, IP scanning) all build directly on these core concepts.
