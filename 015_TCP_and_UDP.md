## UDP& TCP

UDP (User Datagram Protocol) and TCP (Transmission Control Protocol) are both transport layer protocols used to send data across networks, but they have different characteristics and use cases.

UDP is often used in real-time applications like streaming and voice communications. It is fast and lightweight because it doesn’t have much overhead — there are no acknowledgments, sequence numbers, or error checking. 
This means packets can be lost or arrive out of order, but it's generally not an issue in these scenarios since waiting for retransmissions could cause noticeable delays.

TCP, on the other hand, is more reliable. It uses sequence numbers and acknowledgments to ensure that all packets arrive in order and are retransmitted if lost. This makes TCP ideal for applications where accuracy is crucial, like web browsing or financial transactions. 
However, this comes at the cost of additional overhead and slightly slower performance compared to UDP.

In summary:

UDP: Fast, less reliable, suitable for real-time communications (e.g., video streaming). NO AKNOWLEDGEMENT AND NO SEQUENCED NUMBERS.
TCP: Reliable, ensures correct delivery and ordering, suitable for critical data (e.g., banking transactions).Has aknowledgement of receipt packets

## PORTS
**Transport Layer Port Numbers**
- Used to identify conversations and applications as sources and destinations of transmissions.
- Servers provide services over the network by loading applications.
- Examples include web server applications, FTP applications, and mail transport applications.
- A transport layer port is assigned to each service.


**Well-Known Ports**
- Ports below 1024 are called well-known ports.
      - Commonly used ports include:
            - Web server: port 80
            - FTP server: port 21
            - Mail server: port 25
- Clients automatically identify these well-known ports.
      - Web browsers know to use port 80 for web page requests.


**Host Ports**
- Host ports for TCP and UDP are dynamically assigned from the range above 1024.
      - Ports are randomly assigned by the PC.
- Example of a web browser request:
      - Source port is randomly assigned.
      - Destination port is 80 for the web server.


**Communication Process**
- Web server processes requests addressed to its IP and TCP port.
      - Response from web server has destination port 5305 and source port 80.
- Multiple applications can communicate simultaneously.
      - Example with FTP:
            - FTP client uses destination port 21 and a different source port (e.g., 5307).
  
When we use services like DNS, web, email, FTP, IM, and VoIP over the internet, they rely on client/server systems. These services are identified by port numbers, which are numeric identifiers within each data segment used to track specific 
conversations between a client and server. Every data packet includes both a source and destination port.

**Well-known ports (1-1023)**: Reserved for common network applications, like port 80 for HTTP.
**Registered ports (1024-49151)**: Used by organizations for specific applications, like instant messaging.
**Private ports (49152-65535)**: Typically used as source ports for any application.

Some applications may use both TCP and UDP. For example, DNS uses UDP when clients send requests to a DNS server. However, communication between two DNS servers always uses TCP.
Port management is handled by ICANN (Internet Corporation for Assigned Names and Numbers)

## SOCKET PAIRS
The source and destination ports are placed within each segment, which is encapsulated into an IP packet. The IP packet contains the source and destination IP addresses. The combination of an IP address and a port number (either source or destination) is called a socket.

For example, a PC can request FTP and web services from a server simultaneously. The FTP request might use source port 1305 (dynamically generated) and destination port 21 (FTP service), while the web request uses source port 1099 and destination port 80 (HTTP).

Client socket: Example - 192.168.1.5:1099
Server socket: Example - 192.168.1.7:80
These form a socket pair like 192.168.1.5:1099, 192.168.1.7:80. Sockets enable multiple client processes to distinguish themselves, and multiple connections to the same server process to be differentiated. The source port number acts like a return address, allowing responses to reach the correct application via the transport layer.

## THE netstat COMMAND

The netstat command is a useful tool for monitoring active TCP connections and determining potential security threats. By running netstat, you can list the protocols in use, the local address and port numbers, the foreign address and port numbers, and the connection state (such as ESTABLISHED, LISTENING, etc.).
```C:∖> netstat
   
Active Connections
Proto  Local Address           Foreign Address        State
TCP    192.168.1.124:3126      192.168.0.2:139        ESTABLISHED
TCP    192.168.1.124:3158      207.138.126.152:80     ESTABLISHED
TCP    192.168.1.124:3159      207.138.126.169:80     ESTABLISHED
TCP    192.168.1.124:3161      sc.msn.com:80          ESTABLISHED
TCP    192.168.1.124:3166      www.cisco.com:80       ESTABLISHED

Important Information:
Proto: Protocol being used (TCP, UDP).
Local Address: The IP and port number on your local host.
Foreign Address: The IP or domain name and port number of the remote server.
State: The current status of the connection, e.g., ESTABLISHED (active communication), CLOSE_WAIT, etc.
To show numerical IP addresses and port numbers:
Use the -n option: This will prevent resolving hostnames and application names, displaying only raw IP addresses and port numbers, which can be useful for clarity in security analysis.
