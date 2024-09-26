## MAC and IP: compare the roles of MAC and IP

When a host needs to send a message but only knows the destination device's IP address, it must discover the device's MAC address through address resolution. In an Ethernet LAN, each device has two primary types of addresses:
Physical Address (MAC Address): Used for direct communication between Network Interface Cards (NICs) on the same Ethernet network.
Logical Address (IP Address): Used to route packets from the source to the destination, whether on the same network or a remote one.
Layer 2 physical addresses (MAC addresses) are essential for delivering data frames containing encapsulated IP packets within the same network. 
If the destination IP address is on the same network, the corresponding MAC address will belong to the destination device.

When the destination IP address (IPv4 or IPv6) is on a remote network, the destination MAC address will be the address of the host default gateway (i.e., the router interface).

When a host (PC1) needs to send a packet to a destination device (PC2) on a remote network, it uses the MAC address of the local default gateway (router R1) because the destination IP address is not on the same local network. Routers analyze the destination IPv4 address to determine the best forwarding path.

Packet Flow:

PC1 sends an Ethernet frame to R1 with the destination MAC address of R1’s interface (192.168.10.1).
Upon receiving the frame, R1 de-encapsulates it, uses the destination IPv4 address to determine the next hop (R2), and encapsulates the packet in a new frame with R1's MAC address as the source and R2's MAC address as the destination.
Network Diagram:

PC1: IP 192.168.10.10, MAC aa-aa-aa.
R1 G0/0/0: IP 192.168.10.1, MAC bb-bb-bb; G0/0/1: IP 209.165.200.225, MAC cc-cc-cc.
R2 G0/0/1: IP 209.165.200.226, MAC dd-dd-dd; G0/0/0: IP 10.1.1.1, MAC ee-ee-ee.
PC2: IP 10.1.1.10, MAC 55-55-55.
As the packet travels, each link encapsulates the IP packet within a frame specific to the link’s data link technology (e.g., Ethernet).
Final Destination:

When the packet reaches R2, it gets encapsulated again for delivery to PC2, with the destination MAC being that of PC2’s network interface.
Address Resolution:

The process of associating IP addresses with MAC addresses along the path is managed by:
ARP (Address Resolution Protocol) for IPv4 packets.
ICMPv6 Neighbor Discovery for IPv6 packets.

## Broadcast containment

A broadcast MAC address is a special address used in networking to send a packet to all devices on a local area network (LAN) segment.
The broadcast MAC address is composed of 48 bits. This is divided into six octets (or bytes), with each octet consisting of 8 bits. Is represented as FF:FF:FF:FF:FF:FF in hexadecimal notation, where each F corresponds to 4 bits set to 1, totaling 48 bits of 1s. 
This address consists of all bits set to 1.

**Broadcast Domain**
When a host receives a message sent to the broadcast address, it processes the message as if it were directly addressed to it. Broadcast messages are forwarded by switches to all connected hosts within the same local network, which is known as a broadcast domain. 
However, having too many hosts in a single broadcast domain can lead to excessive broadcast traffic, limited by the switches' capabilities. As the network expands, network traffic increases, necessitating the division of the local network into multiple broadcast domains for improved performance. 
Routers are used to create these separate broadcast domains.

**Access Layer Communication**
A Network Interface Card (NIC) on a local Ethernet network only accepts frames if the destination address is either the broadcast MAC address or the NIC's own MAC address. 
Since network applications rely on logical IP addresses, a sending host must determine the corresponding MAC address for a destination IP. 
This is done using the Address Resolution Protocol (ARP) in IPv4 networks, while IPv6 networks use Neighbor Discovery for the same purpose.

**Address Resolution Protocol (ARP)**
ARP uses a three step process to discover and store the MAC address of a host on the local network when only the IPv4 address of the host is known:

The sending host creates and sends a frame addressed to a broadcast MAC address. Contained in the frame is a message with the IPv4 address of the intended destination host.
Each host on the network receives the broadcast frame and compares the IPv4 address inside the message with its configured IPv4 address. The host with the matching IPv4 address sends its MAC address back to the original sending host.
The sending host receives the message and stores the MAC address and IPv4 address information in a table called an ARP table.
When the sending host has the MAC address of the destination host in its ARP table, it can send frames directly to the destination without doing an ARP request. 
Because ARP messages rely on broadcast frames to deliver the requests, all hosts in the local IPv4 network must be in the same broadcast domain.
