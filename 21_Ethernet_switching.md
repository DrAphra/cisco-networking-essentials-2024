## ETHERNET
In the early days of networking, different vendors used proprietary methods that made their equipment incompatible with one another. 
To address this, standards were developed to ensure that network devices could communicate across different brands, facilitating design, development, and competition. 
Although there is no official local area networking standard, Ethernet has become the dominant technology. Ethernet operates at Layers 1 and 2 of the OSI model, defining how data is formatted and transmitted over wired networks, 
making it the de facto standard for most wired LANs.

The Institute of Electrical and Electronics Engineers (IEEE) maintains networking standards, including those for Ethernet and wireless technologies. Each standard is assigned a number related to the committee responsible for it, with 802.3 managing Ethernet standards. Since Ethernet's creation in 1973, it has evolved to offer faster and more flexible versions, contributing to its widespread adoption. For example, 802.3 100BASE-T refers to 100 Mbps Ethernet over twisted-pair cables. Early Ethernet versions operated at 10 Mbps, while modern versions reach speeds of 10 Gbps or higher.

a network with four hosts (H1, H2, H3, and H4) is shown to demonstrate Ethernet addressing. Host H1, with a source MAC address of all A's, sends an Ethernet frame to H3, which has a destination MAC address of all C's. When H1 sends the frame to the switch, the switch forwards it to all ports except the one it came from. Hosts H2 and H4 ignore the frame because their MAC addresses don't match the destination. H3, recognizing the matching destination MAC address, receives and processes the message.

## ETHERNET FRAMES

**Ethernet encapsulation**

Ethernet is one of the two main LAN technologies, alongside wireless LANs (WLANs), and it relies on wired communications such as twisted pair, fiber-optic links, and coaxial cables. Operating at both the data link layer and physical layer, Ethernet encompasses a range of networking technologies defined by the IEEE 802.2 and 802.3 standards. It supports various data bandwidths, including:

10 Mbps
100 Mbps
1 Gbps (1000 Mbps)
10 Gbps (10,000 Mbps)
40 Gbps (40,000 Mbps)
100 Gbps (100,000 Mbps)
Ethernet standards specify protocols for Layer 2 and technologies for Layer 1.

In the OSI model Ethernet is defined by data link layer and physical layer protocols.

**Data link sublayers**

IEEE 802 LAN/MAN protocols, including Ethernet, operate using two sublayers of the data link layer: the Logical Link Control (LLC) and the Media Access Control (MAC).

LLC Sublayer: Defined by IEEE 802.2, this sublayer facilitates communication between the networking software (upper layers) and the device hardware (lower layers). It includes information in the frame that indicates which network layer protocol (e.g., IPv4 or IPv6) is being used, enabling multiple Layer 3 protocols to share the same network interface and media.

MAC Sublayer: This sublayer (such as IEEE 802.3 for Ethernet or 802.11 for wireless) is implemented in hardware and handles data encapsulation and media access control. It provides addressing at the data link layer and integrates with various physical layer technologies.

**MAC Sublayer**

The MAC sublayer is crucial for data encapsulation and media access in Ethernet technology.

Data Encapsulation
IEEE 802.3 data encapsulation involves:

Ethernet Frame: The internal structure of the Ethernet frame.
Ethernet Addressing: Each frame includes both source and destination MAC addresses to facilitate delivery between Ethernet NICs on the same LAN.
Ethernet Error Detection: A frame check sequence (FCS) trailer is included for error detection.
Accessing the Media
The MAC sublayer specifies various Ethernet communication standards over different media types, such as copper and fiber. It includes the IEEE 802.2 LLC sublayer above it, with various Ethernet standards, including:

IEEE 802.3u (Fast Ethernet)
IEEE 802.3z (Gigabit Ethernet over Fiber)
IEEE 802.3ab (Gigabit Ethernet over Copper)
IEEE 802.3ae (10 Gigabit Ethernet over Fiber)
Legacy vs. Modern Ethernet
Legacy Ethernet used a shared, half-duplex medium with a bus topology or hubs, employing a contention-based access method called Carrier Sense Multiple Access with Collision Detection (CSMA/CD). This method ensures that only one device transmits at a time and detects collisions when multiple devices try to transmit simultaneously, using a back-off algorithm for retransmission.

In contrast, modern Ethernet LANs utilize switches that enable full-duplex communications, eliminating the need for CSMA/CD access control.

**ETHERNET FRAME FIELDS**

The minimum Ethernet frame size is 64 bytes, while the maximum is 1518 bytes, covering all bytes from the destination MAC address to the frame check sequence (FCS) field. The preamble is not included in this size description.

Collision Fragments/Runt Frames: Frames shorter than 64 bytes are classified as "collision fragments" or "runt frames" and are automatically discarded by receiving devices.
Jumbo Frames: Frames larger than 1500 bytes are termed "jumbo" or "baby giant frames" and are typically supported by most Fast Ethernet and Gigabit Ethernet switches and NICs.
If a transmitted frame is outside the specified size range, the receiving device will drop it, as such frames are considered invalid and often result from collisions or unwanted signals. The figure accompanying the text illustrates each field in the Ethernet frame, with a table available for further details on the function of each field.

**Preamble and start frame delimiter fields**: The Preamble (7 bytes) and Start Frame Delimiter (SFD), also called the Start of Frame (1 byte), fields are used for synchronization between the sending and receiving devices. These first eight bytes of the frame are used to get the attention of the receiving nodes. Essentially, the first few bytes tell the receivers to get ready to receive a new frame.

**Destination MAC address field**: This 6-byte field is the identifier for the intended recipient. As you will recall, this address is used by Layer 2 to assist devices in determining if a frame is addressed to them. The address in the frame is compared to the MAC address in the device. If there is a match, the device accepts the frame. Can be a unicast, multicast or broadcast address.

**Source MAC address field**: This 6-byte field identifies the originating NIC or interface of the frame.

**Type/length**: This 2-byte field identifies the upper layer protocol encapsulated in the Ethernet frame. Common values are, in hexadecimal, 0x800 for IPv4, 0x86DD for IPv6 and 0x806 for ARP. : You may also see this field referred to as EtherType, Type, or Length.

**Data field**: This field (46 - 1500 bytes) contains the encapsulated data from a higher layer, which is a generic Layer 3 PDU, or more commonly, an IPv4 packet. All frames must be at least 64 bytes long. If a small packet is encapsulated, additional bits called a pad are used to increase the size of the frame to this minimum size.

**Frame check sequence field**: The Frame Check Sequence (FCS) field (4 bytes) is used to detect errors in a frame. It uses a cyclic redundancy check (CRC). The sending device includes the results of a CRC in the FCS field of the frame. The receiving device receives the frame and generates a CRC to look for errors. If the calculations match, no error occurred. Calculations that do not match are an indication that the data has changed; therefore, the frame is dropped. A change in the data could be the result of a disruption of the electrical signals that represent the bits.

## ETHERNET MAC ADDRESS

IPv4 addresses use decimal and binary systems, while IPv6 and Ethernet addresses use hexadecimal. The hexadecimal system uses digits 0-9 and letters A-F, and each hexadecimal digit represents 4 binary bits. Ethernet MAC addresses are 48-bit binary values, expressed using 12 hexadecimal digits. The text also shows how binary, decimal, and hexadecimal values correspond and explains the importance of leading zeroes in hexadecimal. It outlines how to convert between decimal, binary, and hexadecimal for address representation.

**UNICAST MAC ADDRESS**

In Ethernet, different MAC addresses are used for unicast, broadcast, and multicast communications. A unicast MAC address is unique to each device and is used for direct communication between a single sender and receiver. The text describes an example where a host with IPv4 address 192.168.1.5 requests a web page from a server with IPv4 unicast address 192.168.1.200. The Ethernet frame includes both the destination and source MAC and IP addresses. The Address Resolution Protocol (ARP) resolves the destination MAC for IPv4 addresses, while Neighbor Discovery (ND) does the same for IPv6. The source MAC must always be a unicast address.

**BROADCAST MAC ADDRESS**

An Ethernet broadcast frame is processed by every device on the LAN and uses a destination MAC address of FF-FF-FF-FF-FF-FF (48 ones in binary). Broadcast frames are sent to all devices on the network, except the port where the frame originated. These frames are not forwarded by routers. If the data encapsulated in the frame is an IPv4 broadcast packet, it contains a destination IPv4 address with all ones in the host portion, indicating all hosts in the local network will process it. An example is DHCP for IPv4, which uses both Ethernet and IPv4 broadcasts. ARP requests, although not using IPv4, are also sent as Ethernet broadcasts.

**MULTICAST MAC ADDRESS**

An Ethernet multicast frame is processed by a group of devices that belong to the same multicast group on the LAN. The multicast destination MAC address for IPv4 multicast packets begins with 01-00-5E, and for IPv6 it begins with 33-33. These frames are sent to all Ethernet switch ports except the incoming port, unless multicast snooping is configured on the switch. Routers don't forward multicast packets unless configured for multicast routing. Devices in a multicast group are assigned a multicast group IP address. Examples of multicast applications include routing protocols and some multimedia software.

## THE MAC ADDRESS TABLE

**SWITCH FUNDAMENTALS**

An Ethernet switch uses Layer 2 MAC addresses to make forwarding decisions for frames on a network. Unlike Ethernet hubs, which send data out of all ports, switches use a MAC address table to determine the correct port to forward a frame to. The switch is unaware of the data or protocol carried in the frame and focuses solely on the Ethernet MAC addresses to forward or discard the frame. Initially, when a switch is powered on, the MAC address table is empty. As the switch receives frames, it learns the MAC addresses of connected devices and updates the table to efficiently forward frames.

**SWITCH LEARNING AND FORWARDING**

The switch dynamically builds the MAC address table by examining the source MAC address of the frames received on a port. The switch forwards frames by searching for a match between the destination MAC address in the frame and an entry in the MAC address table.

**LEARN - examine the source MAC address**:When a frame enters a switch, the switch examines the source MAC address and the port where the frame arrived. If the source MAC address is new (not in the MAC address table), the switch adds it along with the port number. If the MAC address already exists, the switch refreshes the timer for that entry. If the same MAC address appears from a different port, the switch updates the table with the new port information. Typically, entries in the MAC address table remain for 5 minutes unless updated. In the example, PC-A sends a frame, and the switch adds PC-A's MAC address to the table.

**FORWARD - Find the Destination MAC Address**: When a switch receives a frame with a unicast destination MAC address, it checks its MAC address table for a match. If the address is found, the switch forwards the frame to the specified port. If the address is not found, the switch performs an unknown unicast action by flooding the frame out of all ports except the incoming port.

In the example with PC-D, since the switch does not have the destination MAC address in its table, it forwards the frame out all ports except for the one it received it on. Similarly, if the destination MAC address is a broadcast or multicast, the switch will also flood the frame out of all ports except the incoming port.

## FILTERING FRAMES

As a switch receives frames from different devices, it is able to populate its MAC address table by examining the source MAC address of every frame. When the MAC address table of the switch contains the destination MAC address, it is able to filter the frame and forward out a single port.

**PC-D to switch**: In the figure, PC-D is replying back to PC-A. The switch sees the MAC address of PC-D in the incoming frame on port 4. The switch then puts the MAC address of PC-D into the MAC Address Table associated with port 4.The switch adds the port number and MAC address for PC-D to its MAC address table.

**Switch to PC-A**: Next, because the switch has destination MAC address for PC-A in the MAC Address Table, it will send the frame only out port 1, as shown in the figure.

The switch has a MAC address entry for the destination.
The switch filters the frame, sending it only out port 1.

**PC-A to switch to PC-D**: Next, PC-A sends another frame to PC-D, as shown in the figure. The MAC address table already contains the MAC address for PC-A; therefore, the five-minute refresh timer for that entry is reset. Next, because the switch table contains the destination MAC address for PC-D, it sends the frame only out port 4.

The switch receives another frame from PC-A and refreshes the timer for the MAC address entry for port 1.
The switch has a recent entry for the destination MAC address and filters the frame, forwarding it only out port4.

## SUMMARIES

**Ethernet**
Overview: Ethernet has become the predominant technology for local area networking (LAN), defining how data is formatted and transmitted over wired networks. It operates at Layer 1 and Layer 2 of the OSI model and is considered a de facto standard for almost all wired LANs.

Standards Maintenance: The IEEE (Institute of Electrical and Electronics Engineers) maintains networking standards, including Ethernet and wireless protocols. Each standard is assigned a number, with the 802.3 standard specifically addressing Ethernet technology. The Ethernet standard has evolved over time.

Frame Transmission: Ethernet switches can send a frame out to all ports except the one it was received from. When a frame is received, each host examines the destination MAC address against its own. The Ethernet NIC (Network Interface Card) performs this comparison. If the MAC addresses do not match, the host ignores the frame; if they match, the host receives the entire frame and its contents.

**Ethernet frames**

Protocols: Ethernet is defined by the IEEE 802.2 (Logical Link Control, LLC) and 802.3 (Media Access Control, MAC) protocols. It supports data bandwidths ranging from 10 Mbps to 100 Gbps.

Data Link Layer Sublayers:

LLC Sublayer: This IEEE 802.2 sublayer acts as an interface between the networking software and the hardware. It adds information to the frame that identifies the network layer protocol being used (e.g., IPv4 or IPv6), allowing multiple Layer 3 protocols to share the same network interface and media.
MAC Sublayer: Implemented in hardware (such as IEEE 802.3 for Ethernet), the MAC sublayer is responsible for data encapsulation, media access control, and providing data link layer addressing. It integrates with various physical layer technologies and includes functions like Ethernet framing, addressing, and error detection.
Full-Duplex Communication: Modern Ethernet LANs use switches that operate in full-duplex mode, eliminating the need for access control mechanisms like CSMA/CD (Carrier Sense Multiple Access with Collision Detection).

Ethernet Frame Structure: The minimum Ethernet frame size is 64 bytes, and the maximum is 1518 bytes. The structure of an Ethernet frame includes the following fields:

Preamble and Start Frame Delimiter
Destination MAC Address
Source MAC Address
Type / Length
Data
Frame Check Sequence (FCS)
This structure encompasses all bytes from the destination MAC address field through the FCS field, ensuring effective communication within the network.

**Ethernet MAC address**

Ethernet MAC Address:

An Ethernet MAC address consists of a 48-bit binary value, typically represented in hexadecimal format using 12 hexadecimal digits (each representing 4 bits).
Unicast MAC Address:

A unicast MAC address is a unique identifier used when a frame is sent from one device to another specific device.
The Address Resolution Protocol (ARP) is used to determine the destination MAC address associated with an IPv4 address.
The Neighbor Discovery (ND) protocol is used to determine the destination MAC address associated with an IPv6 address.
Ethernet Broadcast:

Destination MAC Address: FF-FF-FF-FF-FF-FF (48 ones in binary).
The broadcast frame is flooded out to all Ethernet switch ports, except the port it was received from.
Broadcast frames are not forwarded by routers.
Ethernet Multicast:

Destination MAC Address:
01-00-5E for IPv4 multicast packets.
33-33 for IPv6 multicast packets.
Other reserved multicast MAC addresses are used for non-IP protocols, such as Spanning Tree Protocol (STP) and Link Layer Discovery Protocol (LLDP).
Multicast frames are flooded out to all Ethernet switch ports except the incoming port unless the switch is configured for multicast snooping.
Multicast frames are not forwarded by routers unless configured to route multicast packets.

**MAC address table**

Layer 2 Ethernet Switch:

Utilizes Layer 2 MAC addresses for making forwarding decisions and is unaware of the data protocols contained within the frame's payload.
The MAC address table, sometimes called a Content Addressable Memory (CAM) table, is used to determine how frames should be forwarded.
MAC Address Table Population:

The switch dynamically builds its MAC address table by examining the source MAC addresses of incoming frames on its ports.
As frames are received, the switch records the source MAC address along with the corresponding port number in its MAC address table.
Forwarding Frames:

When a frame is received, the switch checks the destination MAC address against its MAC address table:
If the destination MAC address is a unicast address:
If a match is found in the MAC address table, the switch forwards the frame out the specified port.
If no match is found (unknown unicast), the switch floods the frame out all ports except the incoming port.
The switch can filter and forward frames to a single port when the destination MAC address is present in the MAC address table.
Multiple MAC Addresses:

A single switch port can have multiple MAC addresses associated with it, particularly when connected to another switch. Each unique source MAC address results in a separate entry in the MAC address table.
Handling Remote Networks:

When a device needs to send a frame to an IP address on a different network, it cannot send it directly to the destination device's MAC address. Instead, the Ethernet frame is sent to the MAC address of the default gateway (router).







