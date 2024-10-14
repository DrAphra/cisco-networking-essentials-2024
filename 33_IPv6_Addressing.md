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

