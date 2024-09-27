## TROUBLESHOOTING COMMANDS

Most of these utilities that can help identify network problems, are provided by the operating system as command line interface (CLI) commands.
Some of the available utilities include:

**ipconfig** - Displays IP configuration information.

**ping** - Tests connections to other IP hosts.

**netstat** - Displays network connections.

**tracert** - Displays the route taken to the destination.

**nslookup** - Directly queries the name server for information on a destination domain.

## IPCONFIG COMMAND
On Windows devices, you can view the IP configuration information with the ipconfig command at the command prompt. The ipconfig command has several options that are helpful including /all, /release, and /renew.

The **ipconfig** command is used to display the current IP configuration information for a host. Issuing this command from the command prompt will display the basic configuration information including IP address, subnet mask, and default gateway.

The command **ipconfig /all** displays additional information including the MAC address, IP addresses of the default gateway, and the DNS servers. It also indicates if DHCP is enabled, the DHCP server address, and lease information.

the command **ipconfig /release** will release the current DHCP bindings. ipconfig /renew will request fresh configuration information from the DHCP server. A host may contain faulty or outdated IP configuration information and a simple renewal of this information is all that is required to regain connectivity. If, after releasing the IP configuration, the host is unable to obtain fresh information from the DHCP server, it could be that there is no network connectivity. Verify that the NIC has an illuminated link light, indicating that it has a physical connection to the network. If this does not solve the problem, it may be an issue with the DHCP server or network connections to the DCHP server.

The command **ipconfig/renew** is used to request a new IP address from the DHCP server.

## PING COMMAND

Most IP enabled devices support some form of the ping command in order to test whether or not network devices are reachable through the IP network.

If the IP configuration appears to be correctly configured on the local host, next, test network connectivity by using ping. The ping command can be followed by either an IP address or the name of a destination host.

When a ping is sent to an IP address, a packet known as an **echo request** is sent across the network to the IP address specified. If the destination host receives the echo request, it responds with a packet known as an **echo reply**. If the source receives the echo reply, connectivity is verified by the reply from the specific IP address. The ping is not successful if a message such as request timed out or general failure appears.

If a ping command is sent to a name, such as ww​w.cisco.com, a packet is first sent to a DNS server to resolve the name to an IP address. After the IP address is obtained, the echo request is forwarded to the IP address and the process proceeds. If a ping to the IP address succeeds, but a ping to the name does not, there is most likely a problem with DNS.

**Successful Ping but Application Inaccessible**: If both the name and IP address respond to a ping but the application is not accessible, the issue likely lies within the destination application. For instance, the required service might not be running.

**Ping Failures:**

- If neither ping is successful (name or IP), it indicates a network connectivity issue between the source and destination.
- A common step is to ping the default gateway. If successful, the problem is not local, suggesting an issue along the broader network path. If it fails, the problem is on the local network.

**Ping Failure due to Firewalls**: In some cases, ping commands can fail due to firewalls on the sending or receiving device or because a router along the path is blocking ping requests.

**Ping Options:** The basic ping command typically issues four echo requests, but it can be modified with additional options to increase its functionality.
Options:
    -t             Ping the specified host until stopped.
                   To see statistics and continue - type Control-Break;
                   To stop - type Control-C.
    -a             Resolve addresses to hostnames.
    -n count       Number of echo requests to send.
    -l size        Send buffer size.
    -f             Set Don't Fragment flag in packet (IPv4-only).
    -i TTL         Time To Live.
    -v TOS         Type Of Service (IPv4-only. This setting has been deprecated
                   and has no effect on the type of service field in the IP
                   Header).
    -r count       Record route for count hops (IPv4-only).
    -s count       Timestamp for count hops (IPv4-only).
    -j host-list   Loose source route along host-list (IPv4-only).
    -k host-list   Strict source route along host-list (IPv4-only).
    -w timeout     Timeout in milliseconds to wait for each reply.
    -R             Use routing header to test reverse route also (IPv6-only).
                   Per RFC 5095 the use of this routing header has been
                   deprecated. Some systems may drop echo requests if
                   deprecated. Some systems may drop echo requests if
    -S srcaddr     Source address to use.
    -c compartment Routing compartment identifier.
    -p             Ping a Hyper-V Network Virtualization provider address.
    -4             Force using IPv4.
    -6             Force using IPv6.
