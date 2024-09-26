
## NETWORK BOUNDARIES

Every host on a network must use the router as a gateway to other networks. Therefore, each host must know the IPv4 address of the router interface connected to the network where the host is attached. This address is known as the default gateway address. It can be either statically configured on the host or received dynamically by DHCP.
The wireless router acts as a DHCP server for all local hosts attached to it, either by Ethernet cable or wirelessly. These local hosts are referred to as being located on an internal, or inside, network. When a wireless router is connected to the ISP, it acts like a DHCP client to receive the correct external network IPv4 address for the internet interface. ISPs usually provide an internet-routable address, which enables hosts connected to the wireless router to have access to the internet. The wireless router serves as the boundary between the local internal network and the external internet.

**Wireless Router as DHCP Server**: The wireless router assigns IP addresses to devices (local hosts) on the internal network, usually using private IP addresses, which are not accessible from the internet.

**Internal Network**: The devices connected to the wireless router (wired or wireless) form the internal or inside network, with IP addresses in the same range as the router’s internal IP.

**External Network**: The side of the wireless router connected to the ISP is called the external or outside network, using an internet-routable public IP address.

**Default IPv4 Address**: The router’s internal IP address is typically the first address in the network (e.g., 192.168.1.1), and serves as the default gateway for the local devices.

**DHCP Client Role of Router**: The router also acts as a DHCP client to receive its external public IP address from the ISP.

**Boundary Between Networks**: The wireless router separates the internal private network from the external public internet, controlling access and routing traffic.

**Subnet Information**: The router provides connected devices with an IP address, subnet mask, and the router’s internal IP as the default gateway, allowing communication within the network and access to the internet.

This captures the core points related to how routers manage IP addresses and separate internal and external networks.

## NETWORK ADDRESS TRANSLATION

The wireless router receives a public address from the ISP, which allows it to send and receive packets on the internet. It, in turn, provides private addresses to local network clients.

The process used to convert private addresses to internet-routable addresses is called NAT. With NAT, a private (local) source IPv4 address is translated to a public (global) address. The process is reversed for incoming packets. The wireless router is able to translate many internal IPv4 addresses to the same public address, by using NAT.
Only packets destined for other networks need to be translated. These packets must pass through the gateway, where the wireless router replaces the private IPv4 address of the source host with its own public IPv4 address.

**Private IP networks**:
192.168.0.0    255.255.255.0 -> smaller networks (8 bits for host)
172.16.0.0     255.255.0.0   -> medium networks  (16 bits for host)
10.0.0.0.      255.0.0.0     -> larger networks  (24 bits for host)
