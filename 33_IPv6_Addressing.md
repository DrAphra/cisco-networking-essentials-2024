## IPv6 ADDRESS TYPES

**UNICAST, MULTICAST, ANYCAST**

There are three main types of IPv6 addresses:

**Unicast:** Uniquely identifies an interface on an IPv6-enabled device.

**Multicast:** Sends a single packet to multiple destinations.

**Anycast:** Assigned to multiple devices; packets are routed to the nearest device with that address (not covered in this course).

IPv6 does not have a broadcast address like IPv4, but it uses an all-nodes multicast address for similar functionality.

**IPv6 PREFIX LENGTH**

In IPv6, the network portion of an address is called the prefix length, which is represented in slash notation (e.g., /64) and ranges from 0 to 128 bits. Unlike IPv4, IPv6 does not use dotted-decimal subnet masks.

For most networks, including LANs, a /64 prefix length is recommended. This divides the IPv6 address into two parts:

A 64-bit prefix (network portion).
A 64-bit Interface ID (host portion).
Using a 64-bit Interface ID is recommended because it supports stateless address autoconfiguration (SLAAC) and simplifies subnetting.

**TYPES OF IPV6 UNICAST ADDRESSES**

IPv6 unicast addresses uniquely identify an interface on an IPv6-enabled device, and a packet sent to a unicast address is received by that specific interface. A source IPv6 address must always be a unicast address, while the destination can be either unicast or multicast.

There are six main types of IPv6 unicast addresses:

- Global Unicast Address (GUA): Similar to public IPv4 addresses, these are globally unique and internet-routable. - GUAs can be assigned statically or dynamically.
- Link-Local Address (LLA): Required for every IPv6-enabled device, LLAs are used for communication within a local link (subnet). They are not routable beyond that link.
- Loopback (::1/128): Used for local testing on the same device.
- Unspecified Address (::/128): Used when a device has not yet been assigned an address.
- Unique Local Address (fc00::/7 - fdff::/7): Similar to private IPv4 addresses, these are used for local communication and are not routable on the global internet.
- Embedded IPv4: Allows the transition from IPv4 to IPv6 by embedding an IPv4 address within an IPv6 address.

Unique Local Addresses (ULAs) in IPv6, ranging from fc00::/7 to fdff::/7, are used for local addressing within a site or between a limited number of sites. They are not routable on the global internet and are intended for devices that do not require access to external networks, such as internal servers or printers. While RFC 1918 private addresses in IPv4 are sometimes used to obscure networks from potential threats, this was not their intended purpose. Proper security should be implemented on internet-facing routers instead of relying solely on address types for security.

**IPv6 GUA**

IPv6 global unicast addresses (GUAs) are unique and routable on the IPv6 internet, similar to public IPv4 addresses. The Internet Assigned Numbers Authority (IANA) allocates IPv6 address blocks to five Regional Internet Registries (RIRs), and currently, GUAs are assigned from the range starting with the first three bits as 001, specifically from 2000::/3.

GUA Structure:

- Global Routing Prefix: 48 bits.
- Subnet ID: 16 bits.
- Interface ID: 64 bits.
  
The combination of a /48 routing prefix and a 16-bit Subnet ID results in a /64 prefix, which is commonly used in IPv6 addressing.

Address Range:
The first hextet for available GUAs starts from 2000 (binary 0010 0000 0000 0000) to 3fff (binary 0011 1111 1111 1111).

**note** The address 2001:db8::/32 is reserved for documentation and examples, ensuring it doesn't conflict with other address types.
GUAs allow for efficient routing across the internet, with only a small portion of the IPv6 address space allocated for other unicast and multicast addresses.

**Global routing prefix**

The global routing prefix is the network portion of an IPv6 address assigned by an Internet Service Provider (ISP) to a customer or site. ISPs typically assign a /48 global routing prefix, which is common for many organizations. For example, in the IPv6 address 2001:db8:acad::/48, the global routing prefix is 2001:db8
, representing the first 48 bits (3 hextets). The double colon (::) indicates that the remaining address consists of all 0s. The size of the global routing prefix influences the size of the subnet ID.

**Subnet ID**

The subnet ID is the section between the global routing prefix and the interface ID. Unlike IPv4, where bits must be borrowed from the host portion for subnetting, IPv6 was designed to accommodate subnetting natively. Organizations can use the subnet ID to identify different subnets within their network. For example, organizations with a /32 global routing prefix can have up to 4.3 billion subnets, each supporting up to 18 quintillion devices. This vast potential allows organizations to manage large networks effectively.

In a typical IPv6 address with a /48 global routing prefix, the first four hextets are used for the network portion, with the fourth hextet indicating the subnet ID. The remaining hextets are reserved for the interface ID.

**Interface ID**

The interface ID is equivalent to the host portion of an IPv4 address, but the term reflects that a single device may have multiple interfaces, each with its own IPv6 addresses. It is strongly recommended to use a /64 prefix, which provides a 64-bit interface ID. This configuration allows for 18 quintillion hosts per subnet and enables stateless address autoconfiguration (SLAAC) for devices to generate their own interface IDs.

In IPv6, both the all-0s and all-1s addresses can be assigned to devices. The all-1s address can be used since IPv6 does not utilize broadcast addresses. The all-0s address is reserved as a subnet-router anycast address and should only be assigned to routers.

**IPv6 LLA(link-local addresses)**

An IPv6 link-local address (LLA) allows a device to communicate with other IPv6-enabled devices on the same link (subnet) but does not support routing beyond that link. Every IPv6-enabled network interface must have an LLA, while a Global Unicast Address (GUA) is not mandatory.

**Key Features:**
Automatic Configuration: If an LLA is not manually configured, the device will automatically generate one without needing to communicate with a DHCP server. This means devices can still communicate on the local subnet even if they lack a GUA.

Address Range: LLAs fall within the fe80::/10 range. The first 10 bits of an LLA are 1111 1110 10, with the first hextet ranging from fe80 (binary 1111 1110 1000 0000) to febf (binary 1111 1110 1011 1111).

**Uses of IPv6 LLAs:**
Routing Protocol Messages: Routers use LLAs of neighboring routers to send routing updates.
Default Gateway: Hosts typically use the LLA of the local router as their default gateway instead of the GUA.

**Obtaining an LLA:**
Statically: Manually configured by an administrator.
Dynamically: Automatically created by the device, either by using randomly generated values or the Extended Unique Identifier (EUI) method, which combines the device's MAC address with additional bits.

**Communication Example**
Devices communicate using their LLAs without routing the packets outside their local link. For instance, a PC can directly communicate with a printer using LLAs, demonstrating the link-local communication that remains within the subnet.

## GUA AND LLA STATIC CONFIGURATION

**ON A ROUTER**

IPv6 Global Unicast Addresses (GUAs) are equivalent to public IPv4 addresses, being globally unique and routable on the IPv6 internet. An IPv6 Link-Local Address (LLA) allows communication between two IPv6-enabled devices on the same link (subnet). This section covers how to statically configure IPv6 GUAs and LLAs on routers.

Most IPv6 configuration and verification commands in Cisco IOS are similar to their IPv4 counterparts. The key difference is the use of `ipv6` instead of `ip` in the commands.

## Command Examples

- To configure an IPv4 address on an interface:
    ```
    ip address ip-address subnet-mask
    ```

- To configure an IPv6 GUA on an interface:
    ```
    ipv6 address ipv6-address/prefix-length
    ```
  > **Note**: There is no space between `ipv6-address` and `prefix-length`.

## Example Configuration

The following IPv6 subnets will be used:
- `2001:db8:acad:1::/64`
- `2001:db8:acad:2::/64`
- `2001:db8:acad:3::/64`

### Example Topology
- **PC1**: `2001:db8:acad:1::10/64` (connected to a switch, which connects to R1's G0/0/0 interface)
- **PC2**: `2001:db8:acad:2::10/64` (connected to a switch, which connects to R1's G0/0/1 interface)
- **Router R1**:
  - G0/0/0: `2001:db8:acad:1::1/64`
  - G0/0/1: `2001:db8:acad:2::1/64`
  - S0/1/0: `2001:db8:acad:3::1/64`

## IPv6 GUA Configuration on Router R1

```bash
R1(config)# interface gigabitethernet 0/0/0
R1(config-if)# ipv6 address 2001:db8:acad:1::1/64
R1(config-if)# no shutdown
R1(config-if)# exit

R1(config)# interface gigabitethernet 0/0/1
R1(config-if)# ipv6 address 2001:db8:acad:2::1/64
R1(config-if)# no shutdown
R1(config-if)# exit

R1(config)# interface serial 0/1/0
R1(config-if)# ipv6 address 2001:db8:acad:3::1/64
R1(config-if)# no shutdown

## Static GUA configuration on a Windows host 

Manually configuring the IPv6 address on a Windows host is similar to configuring an IPv4 address. 

- The default gateway address configured for **PC1** is `2001:db8:acad:1::1`, which is the GUA of the R1 GigabitEthernet interface on the same network.
- Alternatively, the default gateway can match the LLA of the GigabitEthernet interface. Using the LLA of the router as the default gateway is considered best practice.

## Windows Internet Protocol Version 6 (TCP/IPv6) Properties

The configuration window shows:
- **Use the following IPv6 address**: `2001:db8:acad:1::1`
- **Subnet prefix length**: `64`
- **Default gateway**: `2001:db8:acad:1::1`
- **Use the following DNS server address**: selected

Just like with IPv4, configuring static addresses on clients does not scale well in larger environments. Therefore, most network administrators will enable dynamic assignment of IPv6 addresses.

### Automatic IPv6 GUA Acquisition

There are two ways a device can automatically obtain an IPv6 GUA:
- Stateless Address Autoconfiguration (SLAAC)
- Stateful DHCPv6

> **Note**: When using DHCPv6 or SLAAC, the LLA of the router will automatically be set as the default gateway address.

markdown
Copy code
# 33.2.3 Static Configuration of a Link-Local Unicast Address

Manually configuring a Link-Local Address (LLA) allows you to create addresses that are recognizable and easier to remember. This is particularly useful for routers, as their LLAs are used as default gateway addresses and in routing advertisement messages.

- LLAs can be configured manually using the command:
  
  ```bash
  ipv6 address ipv6-link-local-address link-local
An address starting with the hextet in the range of fe80 to febf must include the link-local parameter.
Example Topology with LLAs
The example topology includes:

PC1 connected to a switch with IPv6 address: 2001:db8:acad:1::10/64
PC2 connected to a switch with IPv6 address: 2001:db8:acad:2::10/64
Router R1 has:
G0/0/0 interface with IPv6 address: 2001:db8:acad:1::1/64 and LLA: fe80::1:1
G0/0/1 interface with IPv6 address: 2001:db8:acad:2::1/64 and LLA: fe80::2:1
S0/1/0 interface with IPv6 address: 2001:db8:acad:3::1/64 and LLA: fe80::3:1
Configuration of LLAs on Router R1
The example commands to configure an LLA on router R1 are as follows:

bash
```
R1(config)# interface gigabitethernet 0/0/0
R1(config-if)# ipv6 address fe80::1:1 link-local
R1(config-if)# exit
R1(config)# interface gigabitethernet 0/0/1
R1(config-if)# ipv6 address fe80::2:1 link-local
R1(config-if)# exit
R1(config)# interface serial 0/1/0
R1(config-if)# ipv6 address fe80::3:1 link-local
R1(config-if)# exit
Statically configured LLAs help in easily identifying router R1. In this example, all interfaces of router R1 are configured with LLAs that start with fe80::n:1.

Note: The same LLA can be configured on each link as long as it is unique on that link. However, it is common practice to create different LLAs for each interface of the router for easier identification.

## DYNAMIC ADDRESSING FOR IPV6 GUAS

# Dynamic Addressing for IPv6

To better understand dynamic addressing for IPv6, let's first look at DHCP for IPv4. 

- **PC1** and **PC2** have both received their IPv4 addressing information from a DHCP server.
- Most of this information, including:
  - Subnet mask
  - Default gateway address
  - DNS server address
  
  is not unique and is the same information sent to all clients. This information is considered **stateless**.

- This means that a DHCP server is not maintaining state or keeping a record of who receives this information.

- However, the IPv4 addresses for each device are assigned from a pool with each device getting a unique IPv4 address. This information is considered **stateful**.

- The DHCP server maintains state by keeping a record of which device receives which IPv4 address based on the client's Ethernet MAC address.

- Notice that although each IPv4 address is unique, the network portion of the addresses is the same; only the host portion makes each address unique.

## Dynamic Addressing with IPv6

Dynamic addressing with IPv6 uses an **ICMPv6 router advertisement message**, which informs the clients how to dynamically obtain their IPv6 addressing information.

- An IPv6 router sends out router advertisement messages periodically. Cisco routers send them every **200 seconds**.
- An RA message may also be sent anytime the router receives a **router solicitation message** from a device.

### Router Advertisement (RA) Message

- A router advertisement message is sent to the all IPv6 devices multicast address, **FF02::1**.
- The source IPv6 address of the RA message is the link-local address of the router, which in this case is **FE80::1**.
- The RA message includes:
  - The network prefix
  - Prefix length (same network prefix as the router's global unicast address on this interface)
  - A DNS server address
  - One or more of the following configuration flags enabled.

Both **PC1** and **PC2** have received the RA message. The components include:
- The network prefix and prefix length indicate their network address.
- The source IPv6 address provides the devices their default gateway address.
- The address of one or more DNS servers is typically included in the RA message.

In this example, the RA message only has the **A** flag enabled, meaning that our devices will use **SLAAC** (Stateless Address Autoconfiguration) for their IPv6 global unicast addresses.

- **PC1** uses the network prefix information from the RA message and randomly creates its own **interface ID** (the host portion of the address).
- The interface ID is indicated in red.
- **PC2** does the same.

Notice that all the address information obtained by **PC1** and **PC2** is stateless; there is no server keeping track of which device has received which address. This means that a stateful DHCP server is not required.

# RS and RA Messages

If you do not want to statically configure IPv6 GUAs, there is no need to worry. Most devices obtain their IPv6 GUAs dynamically. This topic explains how this process works using **Router Advertisement (RA)** and **Router Solicitation (RS)** messages. This topic gets rather technical, but understanding the difference between the three methods that a router advertisement can use, as well as how the **EUI-64 process** for creating an interface ID differs from a randomly generated process, will enhance your IPv6 expertise!

## Dynamic Addressing with ICMPv6

For the GUA, a device obtains the address dynamically through **Internet Control Message Protocol version 6 (ICMPv6)** messages. 

- IPv6 routers periodically send out ICMPv6 RA messages every **200 seconds** to all IPv6-enabled devices on the network.
- An RA message will also be sent in response to a host sending an ICMPv6 RS message, which is a request for an RA message.

### ICMPv6 RS and RA Messages

- **RS messages** are sent to all IPv6 routers by hosts requesting addressing information.
- **RA messages** are sent to all IPv6 nodes.

If **Method 1** (SLAAC only) is used, the RA includes:
- Network prefix
- Prefix-length
- Default-gateway information

RA messages are on IPv6 router Ethernet interfaces. The router must be enabled for IPv6 routing, which is not enabled by default. To enable a router as an IPv6 router, the `ipv6 unicast-routing` global configuration command must be used.

The ICMPv6 RA message is a suggestion to a device on how to obtain an IPv6 GUA. The ultimate decision is up to the device operating system. The ICMPv6 RA message includes the following:

- **Network prefix and prefix length** - This tells the device which network it belongs to.
- **Default gateway address** - This is an IPv6 LLA, the source IPv6 address of the RA message.
- **DNS addresses and domain name** - These are the addresses of DNS servers and a domain name.

### Methods for RA Messages

There are three methods for RA messages:

- **Method 1: SLAAC** - “I have everything you need including the prefix, prefix length, and default gateway address.”
- **Method 2: SLAAC with a stateless DHCPv6 server** - “Here is my information, but you need to get other information such as DNS addresses from a stateless DHCPv6 server.”
- **Method 3: Stateful DHCPv6 (no SLAAC)** - “I can give you your default gateway address. You need to ask a stateful DHCPv6 server for all your other information.”

# Method 1: SLAAC

**SLAAC** (Stateless Address Autoconfiguration) is a method that allows a device to create its own **Global Unicast Address (GUA)** without the services of **DHCPv6**. Using SLAAC, devices rely on the **ICMPv6 Router Advertisement (RA)** messages of the local router to obtain the necessary information.

By default, the RA message suggests that the receiving device use the information in the RA message to create its own IPv6 GUA and all other necessary information. The services of a DHCPv6 server are not required.

SLAAC is stateless, which means there is no central server (for example, a stateful DHCPv6 server) allocating GUAs and keeping a list of devices and their addresses. With SLAAC, the client device uses the information in the RA message to create its own GUA. As shown in the figure, the two parts of the address are created as follows:

- **Prefix** - This is advertised in the RA message.
- **Interface ID** - This uses the **EUI-64 process** or by generating a random 64-bit number, depending on the device operating system.

The router sends an RA message with the prefix for the local link. The PC uses SLAAC to obtain a prefix from the RA message and creates its own Interface ID.

# Method 2: SLAAC and Stateless DHCPv6

A router interface can be configured to send a router advertisement using **SLAAC** and **stateless DHCPv6**.

With this method, the RA message suggests devices use the following:

- **SLAAC** to create its own **IPv6 GUA**
- The router **Link-Local Address (LLA)**, which is the RA source IPv6 address, as the default gateway address
- A stateless **DHCPv6 server** to obtain other information such as a DNS server address and a domain name

> **Note:** A stateless DHCPv6 server distributes DNS server addresses and domain names. It does not allocate GUAs.

The process works as follows:

1. The PC sends a **Router Solicitation (RS)** message to all IPv6 routers, saying, “I need addressing information.”
2. The router sends an RA message to all IPv6 nodes with Method 2 (SLAAC and DHCPv6) specified, stating, “Here is your prefix, prefix-length, and default gateway information. But you will need to get DNS information from a DHCPv6 server.”
3. The PC sends a **DHCPv6 Solicit** message to all DHCPv6 servers, saying, "I used SLAAC to create my IPv6 address and get my default gateway address, but I need other information from a stateless DHCPv6 server."

# Method 3: Stateful DHCPv6

A router interface can be configured to send an **RA** using **stateful DHCPv6** only.

Stateful DHCPv6 is similar to DHCP for IPv4. A device can automatically receive its addressing information, including a **GUA**, prefix length, and the addresses of DNS servers from a stateful DHCPv6 server.

With this method, the RA message suggests devices use the following:

- The router **Link-Local Address (LLA)**, which is the RA source IPv6 address, for the default gateway address.
- A stateful **DHCPv6 server** to obtain a GUA, DNS server address, domain name, and other necessary information.

The process works as follows:

1. The PC sends a **Router Solicitation (RS)** message to all IPv6 routers, saying, “I need addressing information.”
2. The router sends an RA message to all IPv6 nodes with Method 3 (Stateful DHCPv6) specified, stating, “I am your default gateway, but you need to ask a stateful DHCPv6 server for your IPv6 address and other addressing information."
3. The PC sends a **DHCPv6 Solicit** message to all DHCPv6 servers, saying, "I received my default gateway address from the RA message, but I need an IPv6 address and all other addressing information from a stateful DHCPv6 server."

A stateful DHCPv6 server allocates and maintains a list of which device receives which IPv6 address. DHCP for IPv4 is stateful.

> **Note:** The default gateway address can only be obtained dynamically from the RA message. The stateless or stateful DHCPv6 server does not provide the default gateway address.

# EUI-64 Process vs. Randomly Generated

When the **RA** message is either **SLAAC** or **SLAAC with stateless DHCPv6**, the client must generate its own **interface ID**. The client knows the prefix portion of the address from the RA message but must create its own interface ID. The interface ID can be created using the **EUI-64** process or a randomly generated 64-bit number.

## Dynamically Creating an Interface ID

1. The router sends an RA message.
2. The PC uses the prefix in the RA message and uses either EUI-64 or a random 64-bit number to generate an interface ID.

# EUI-64 Process

IEEE defined the **Extended Unique Identifier (EUI)** or modified EUI-64 process. This process uses the **48-bit Ethernet MAC address** of a client and inserts another **16 bits** in the middle of the 48-bit MAC address to create a **64-bit interface ID**.

Ethernet MAC addresses are usually represented in hexadecimal and are made up of two parts:

- **Organizationally Unique Identifier (OUI)** - The OUI is a **24-bit (6 hexadecimal digits)** vendor code assigned by IEEE.
- **Device Identifier** - The device identifier is a unique **24-bit (6 hexadecimal digits)** value within a common OUI.

An **EUI-64 interface ID** is represented in binary and is made up of three parts:

1. **24-bit OUI** from the client MAC address, but the 7th bit (the Universally/Locally (U/L) bit) is reversed. This means that if the 7th bit is a 0, it becomes a 1, and vice versa.
2. The inserted **16-bit value** `fffe` (in hexadecimal).
3. **24-bit device identifier** from the client MAC address.

The EUI-64 process is illustrated using the R1 GigabitEthernet MAC address of `fc99:4775:cee0`.

### Steps to Generate EUI-64

**Step 1:** Divide the MAC address between the OUI and device identifier.

**Step 2:** Insert the hexadecimal value `fffe`, which in binary is: `1111 1111 1111 1110`.

**Step 3:** Convert the first 2 hexadecimal values of the OUI to binary and flip the U/L bit (bit 7). In this example, the 0 in bit 7 is changed to a 1.

The result is an **EUI-64 generated interface ID** of `fe99:47ff:fe75:cee0`.

**Note:** The use of the U/L bit and the reasons for reversing its value are discussed in [RFC 5342](https://tools.ietf.org/html/rfc5342).

The example output for the `ipconfig` command shows the **IPv6 GUA** being dynamically created using **SLAAC** and the **EUI-64 process**. An easy way to identify that an address was probably created using EUI-64 is by observing the `fffe` located in the middle of the interface ID.

The advantage of **EUI-64** is that the Ethernet MAC address can be used to determine the interface ID. It also allows network administrators to easily track an IPv6 address to an end device using the unique MAC address. However, this has caused privacy concerns among many users who worry that their packets could be traced to the actual physical computer. Due to these concerns, a randomly generated interface ID may be used instead.

# Randomly Generated Interface IDs

Depending upon the operating system, a device may use a **randomly generated interface ID** instead of using the MAC address and the **EUI-64 process**. Beginning with **Windows Vista**, Windows uses a randomly generated interface ID instead of one created with EUI-64. **Windows XP** and previous Windows operating systems used EUI-64.

After the interface ID is established, either through the EUI-64 process or through random generation, it can be combined with an IPv6 prefix in the RA message to create a **GUA**, as shown in the figure.


**Note:** To ensure the uniqueness of any IPv6 unicast address, the client may use a process known as **duplicate address detection (DAD)**. This is similar to an **ARP** request for its own address. If there is no reply, then the address is unique.

## DYNAMIC ADDRESSING FOR IPV6 LLAs

# Dynamic LLAs

All IPv6 devices must have an **IPv6 Link-Local Address (LLA)**. Like IPv6 Global Unicast Addresses (GUAs), you can also create LLAs dynamically. Regardless of how you create your LLAs (and your GUAs), it is important that you verify all IPv6 address configuration. This topic explains dynamically generated LLAs and IPv6 configuration verification.

The LLA is dynamically created using the **fe80::/10** prefix and the interface ID, which can be generated using either the **EUI-64 process** or a randomly generated 64-bit number.

Operating systems, such as Windows, will typically use the same method for both a SLAAC-created GUA and a dynamically assigned LLA.

# Dynamic LLAs on Cisco Routers

Cisco routers automatically create an IPv6 Link-Local Address (LLA) whenever a Global Unicast Address (GUA) is assigned to the interface. By default, Cisco IOS routers use **EUI-64** to generate the interface ID for all LLAs on IPv6 interfaces. For serial interfaces, the router will use the MAC address of an Ethernet interface. Recall that an LLA must be unique only on that link or network. However, a drawback to using the dynamically assigned LLA is its long interface ID, which makes it challenging to identify and remember assigned addresses. 

The example displays the MAC address on the **GigabitEthernet 0/0/0** interface of router **R1**. This address is used to dynamically create the LLA on the same interface, and also for the **Serial 0/1/0** interface.

To make it easier to recognize and remember these addresses on routers, it is common to statically configure IPv6 LLAs on routers.

The show ipv6 interface brief command displays the IPv6 address of the Ethernet interfaces. EUI-64 uses this MAC address to generate the interface ID for the LLA. Additionally, the show ipv6 interface brief command displays abbreviated output for each of the interfaces. The [up/up] output on the same line as the interface indicates the Layer 1/Layer 2 interface state. This is the same as the Status and Protocol columns in the equivalent IPv4 command.

Notice that each interface has two IPv6 addresses. The second address for each interface is the GUA that was configured. The first address, the one that begins with fe80, is the link-local unicast address for the interface. Recall that the LLA is automatically added to the interface when a GUA is assigned.

Also, notice that the R1 Serial 0/1/0 LLA is the same as its GigabitEthernet 0/0/0 interface. Serial interfaces do not have Ethernet MAC addresses, so Cisco IOS uses the MAC address of the first available Ethernet interface. This is possible because link-local interfaces only have to be unique on that link.

the show ipv6 route command can be used to verify that IPv6 networks and specific IPv6 interface addresses have been installed in the IPv6 routing table. The show ipv6 route command will only display IPv6 networks, not IPv4 networks.

Within the route table, a C next to a route indicates that this is a directly connected network. When the router interface is configured with a GUA and is in the “up/up” state, the IPv6 prefix and prefix length is added to the IPv6 routing table as a connected route.

Note: The L indicates a local route, the specific IPv6 address assigned to the interface. This is not an LLA. LLAs are not included in the routing table of the router because they are not routable addresses.

The IPv6 GUA configured on the interface is also installed in the routing table as a local route. The local route has a /128 prefix. Local routes are used by the routing table to efficiently process packets with a destination address of the router interface address.

The ping command for IPv6 is identical to the command used with IPv4, except that an IPv6 address is used. As shown in the example, the command is used to verify Layer 3 connectivity between R1 and PC1. When pinging an LLA from a router, Cisco IOS will prompt the user for the exit interface. Because the destination LLA can be on one or more of its links or networks, the router needs to know which interface to send the ping to.

## IPV6 MULTICAST ADDRESSES

# Assigned IPv6 Multicast Addresses

Earlier in this module, you learned that there are three broad categories of IPv6 addresses: **unicast**, **anycast**, and **multicast**. This topic goes into more detail about multicast addresses.

IPv6 multicast addresses are similar to IPv4 multicast addresses. Recall that a multicast address is used to send a single packet to one or more destinations (multicast group). IPv6 multicast addresses have the prefix **ff00::/8**.

**Note:** Multicast addresses can only be destination addresses and not source addresses.

## Types of IPv6 Multicast Addresses

There are two types of IPv6 multicast addresses:

1. **Well-known multicast addresses**
2. **Solicited-node multicast addresses**

### 33.5.2 Well-Known IPv6 Multicast Addresses

Well-known IPv6 multicast addresses are assigned addresses reserved for predefined groups of devices. An assigned multicast address is a single address used to reach a group of devices running a common protocol or service. Assigned multicast addresses are used in context with specific protocols such as **DHCPv6**.

#### Common IPv6 Assigned Multicast Groups

- **ff02::1 All-nodes multicast group**: This multicast group includes all IPv6-enabled devices. A packet sent to this group is received and processed by all IPv6 interfaces on the link or network. This has the same effect as a broadcast address in IPv4. An example of communication using the all-nodes multicast address is when an IPv6 router sends **ICMPv6 RA messages** to the all-node multicast group.

- **ff02::2 All-routers multicast group**: This multicast group includes all IPv6 routers. A router becomes a member of this group when it is enabled as an IPv6 router with the `ipv6 unicast-routing` global configuration command. A packet sent to this group is received and processed by all IPv6 routers on the link or network.

#### IPv6 All-Nodes Multicast: RA Message

IPv6-enabled devices send **ICMPv6 RS messages** to the all-routers multicast address. The RS message requests an RA message from the IPv6 router to assist the device in its address configuration. The IPv6 router responds with an RA message, as shown.

### 33.5.3 Solicited-Node IPv6 Multicast Addresses

A solicited-node multicast address is similar to the all-nodes multicast address. The advantage of a solicited-node multicast address is that it is mapped to a special Ethernet multicast address. This allows the Ethernet NIC to filter the frame by examining the destination MAC address without sending it to the IPv6 process to see if the device is the intended target of the IPv6 packet.

## SUMMARY

**IPV6 ADDRESS TYPES**
There are three types of IPv6 addresses: unicast, multicast, and anycast. IPv6 does not use the dotted-decimal subnet mask notation. Like IPv4, the prefix length is represented in slash notation and is used to indicate the network portion of an IPv6 address. An IPv6 unicast address uniquely identifies an interface on an IPv6-enabled device. IPv6 addresses typically have two unicast addresses: GUA and LLA. IPv6 unique local addresses have the following uses: they are used for local addressing within a site or between a limited number of sites, they can be used for devices that will never need to access another network, and they are not globally routed or translated to a global IPv6 address. IPv6 global unicast addresses (GUAs) are globally unique and routable on the IPv6 internet. These addresses are equivalent to public IPv4 addresses. A GUA has three parts: a global routing prefix, a subnet ID, and an interface ID. An IPv6 link-local address (LLA) enables a device to communicate with other IPv6-enabled devices on the same link and only on that link (subnet). Devices can obtain an LLA either statically or dynamically.

**GUA AND LLA STATIC CONFIGURATION**
The Cisco IOS command to configure an IPv4 address on an interface is ip address ip-address subnet-mask. In contrast, the command to configure an IPv6 GUA on an interface is ipv6 address ipv6-address/prefix-length. Just as with IPv4, configuring static addresses on clients does not scale to larger environments. For this reason, most network administrators in an IPv6 network will enable dynamic assignment of IPv6 addresses. Configuring the LLA manually lets you create an address that is recognizable and easier to remember. Typically, it is only necessary to create recognizable LLAs on routers. LLAs can be configured manually using the ipv6 address ipv6-link-local-address link-local command.

**DYNAMIC ADDRESSING FOR IPV6 GUAs**
A device obtains a GUA dynamically through ICMPv6 messages. IPv6 routers periodically send out ICMPv6 RA messages, every 200 seconds, to all IPv6-enabled devices on the network. An RA message will also be sent in response to a host sending an ICMPv6 RS message, which is a request for an RA message. The ICMPv6 RA message includes: network prefix and prefix length, default gateway address, and the DNS addresses and domain name. RA messages have three methods: SLAAC, SLAAC with a stateless DHCPv6 server, and stateful DHCPv6 (no SLAAC). With SLAAC, the client device uses the information in the RA message to create its own GUA because the message contains the prefix and the interface ID. With SLAAC with stateless DHCPv6 the RA message suggests devices use SLAAC to create their own IPv6 GUA, use the router LLA as the default gateway address, and use a stateless DHCPv6 server to obtain other necessary information.

With stateful DHCPv6 the RA suggests that devices use the router LLA as the default gateway address, and the stateful DHCPv6 server to obtain a GUA, a DNS server address, domain name and all other necessary information. The interface ID can be created using the EUI-64 process or a randomly generated 64-bit number. The EUIs process uses the 48-bit Ethernet MAC address of the client and inserts another 16 bits in the middle of MAC address to create a 64-bit interface ID. Depending upon the operating system, a device may use a randomly generated interface ID.

**DYNAMIC ADDRESSING FOR IPV6 LLAs**
All IPv6 devices must have an IPv6 LLA. An LLA can be configured manually or created dynamically. Operating systems, such as Windows, will typically use the same method for both a SLAAC-created GUA and a dynamically assigned LLA. Cisco routers automatically create an IPv6 LLA whenever a GUA is assigned to the interface. By default, Cisco IOS routers use EUI-64 to generate the Interface ID for all LLAs on IPv6 interfaces. For serial interfaces, the router will use the MAC address of an Ethernet interface. To make it easier to recognize and remember these addresses on routers, it is common to statically configure IPv6 LLAs on routers. To verify IPv6 address configuration use the following three commands: show ipv6 interface brief, show ipv6 route, and ping.

**IPV6 MULTICAST ADDRESSES**
There are two types of IPv6 multicast addresses: well-known multicast addresses and solicited-node multicast addresses. Assigned multicast addresses are reserved multicast addresses for predefined groups of devices. Well-known multicast addresses are assigned. Two commonIPv6 assigned multicast groups are: ff02::1 All-nodes multicast group and ff02::2 All-routers multicast group. A solicited-node multicast address is similar to the all-nodes multicast address. The advantage of a solicited-node multicast address is that it is mapped to a special Ethernet multicast address.
