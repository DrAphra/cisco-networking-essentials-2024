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




