##THE NEED FOR ROUTING

When devices need to connect beyond their local network to other networks or the internet, routers are used. A router connects multiple IP networks (Layer 3) and determines the best path for sending data. Unlike switches, 
which use MAC addresses (layer 2), routers use IP addresses to make forwarding decisions. If the source and destination devices are on different networks, the router forwards the message by reading the destination IP address, 
re-encapsulating the data, and sending it to the appropriate network.

Routers use routing tables to move data between networks, storing network addresses and the best paths to reach them. Routing tables can be updated dynamically by other routers or manually by administrators. 
Routers rely on these tables to decide where to forward data. If no route is found, the message is dropped. To prevent this, network administrators configure a static default route, 
which allows routers to forward packets with unknown destination addresses, typically to another router that can direct the packet further.

**Type** - The connection type. C stands for directly connected.
**Network** - The network address.
**Port** - The interface used to forward packets to the network.

As networks grow, it is often necessary to divide one access layer network into multiple access layer networks. There are many ways to divide networks based on different criteria:

**Broadcast containment** - Routers in the distribution layer can limit broadcasts to the local network where they need to be heard.
**Security requirements** - Routers in the distribution layer can separate and protect certain groups of computers where confidential information resides.
**Physical locations** - Routers in the distribution layer can be used to interconnect local networks at various locations of an organization that are geographically separated.
**Logical grouping** - Routers in the distribution layer can be used to logically group users, such as departments within a company, who have common needs or for access to resources.
The distribution layer connects these independent local networks and controls the traffic flowing between them. It is responsible for ensuring that traffic between hosts on the local network stays local.

A router is a networking device that connects multiple Layer 3, IP networks. At the distribution layer of the network, routers direct traffic and perform other functions critical to efficient network operation. Routers, like switches, are able to decode and read the messages that are sent to them. Unlike switches, which make their forwarding decision based on the Layer 2 MAC address, routers make their forwarding decision based on the Layer 3 IP address.

Anytime the network portion of the IP addresses of the source and destination hosts do not match, a router must be used to forward the message.

##THE DEFAULT GATEWAY

When a host sends a message to another host on the same network, it uses ARP to find the destination's MAC address, and the message is sent directly. However, when sending to a remote network, the message must go through a router. 
The host includes the destination IP in the packet but uses the router's MAC address in the frame. The router's MAC address is discovered through ARP using the default gateway, which is the router's IP address configured in the host's TCP/IP settings. 
If the default gateway is missing or incorrect, messages to remote networks cannot be sent.

##LAN - LOCAL AREA NETWORK

A local area network (LAN) refers to a group of interconnected local networks under the same administrative control. While originally confined to small, single-location networks, LANs now include networks spanning multiple buildings or locations, 
often with hundreds of hosts. LANs typically use Ethernet or wireless protocols and support high data rates. An "intranet" refers to a private LAN that is accessible only to authorized users within an organization.
Within a LAN, it is possible to place all hosts on a single local network or divide them up between multiple networks connected by a distribution layer device. How this placement is determined depends on desired results.

**All hosts in one local segmente**
Placing all hosts on a single local network allows them to be seen by all other hosts. This is because there is one broadcast domain and hosts use ARP to find each other.

In a simple network design, it may be beneficial to keep all hosts within a single local network. However, as networks grow in size, increased traffic will decrease network performance and speed. In this case, it may be beneficial to move some hosts onto a remote network.

Advantages of a single local segment:

Appropriate for simpler networks
Less complexity and lower network cost
Allows devices to be "seen" by other devices
Faster data transfer - more direct communication
Ease of device access
Disadvantages of a single local segment:

All hosts are in one broadcast domain which causes more traffic on the segment and may slow network performance
Harder to implement QoS
Harder to implement security

**Hosts on a remote segments**
Placing additional hosts on a remote network will decrease the impact of traffic demands. However, hosts on one network will not be able to communicate with hosts on the other network without the use of routing. Routers increase the complexity of the network configuration and can introduce latency, or time delay, on packets sent from one local network to the other.

Advantages:

More appropriate for larger, more complex networks
Splits up broadcast domains and decreases traffic
Can improve performance on each segment
Makes the machines invisible to those on other local network segments
Can provide increased security
Can improve network organization
Disadvantages:

Requires the use of routing (distribution layer)
Router can slow traffic between segments
More complexity and expense (requires a router)
The hosts on a remote segment figure shows network 192 dot 168 dot 1 dot 0 with hosts H1 through H5 connected to Switch 1. Switch 1 connects to Router 1. Router 1 also connects to Switch 2, which is connected to hosts H6 through H10. Text above the figure: Placing additional hosts on a remote network will decrease the impact of traffic demands. However, hosts on one network will not be able to communicate with hosts on the other without the use of routing. Routers increase the complexity of the network configuration and can introduce latency, or time delay, on packets sent from one local network to the other. Advantages: more appropriate for larger, more complex networks, splits up broadcast domains and decreases traffic, can improve performance on each segment, makes the machines invisible to those on other local network segments, can provide increased security, can improve network organization. Disadvantages: requires the use of routing (distribution layer), router can slow traffic between segments, more complexity and expense (requires a router).
