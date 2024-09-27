## CLIENT AND SERVER INTERACTION

Every day, we utilize various services over networks and the internet for communication and daily tasks, often without considering the underlying servers, clients, and networking devices involved.

**Servers** are hosts running software applications that provide information or services to other connected hosts, such as web servers that enable access to websites, email, financial transactions, and music downloads. The functionality of these interactions relies on agreed-upon standards and protocols.

**Clients**, like web browsers (e.g., Chrome, Firefox), are software applications that allow users to access these services. A single computer can run multiple client applications simultaneously, enabling users to check emails, browse web pages, engage in instant messaging, and stream audio concurrently.

3 common types of server software:
- email: email server runs email server software. Clients use mail client software(e.g. Microsoft Outlook) to access email on the server.
- web: web server runs web server software. Clients use browser software (e.g. Chrome or Firefox) to access web pages on the server.
- file: file server stores corporate and user files in a central location. The client devices access these files with client software (e.g. Windows File Explorer).

**Web Client and Web Server Interaction**
- Web client retrieves a web page from the web server.
      - Web server listens for requests on port 80, TCP.
      - Web client uses URL www.learnip.com to initiate the request.
- URL Translation: URL must be translated to an IP address before transmission
      - DNS lookup sends a request to the DNS server to get the associated IP address.
      - IP address returned for www.learnip.com is 172.16.10.50.
  
**TCP Connection Establishment**
- TCP connection created between web server and web client.
      - Web client IP address set to 192.168.10.15 with a random port 5507.
      - Connection is between source 192.168.10.15:5507 and destination 172.16.10.50:80.

The connection is identified by a socket, representing the unique combination of the source and destination IP addresses and port numbers (the socket identifies all components in the conversation)
Once the web server receives the packet, it processes the request by placing it in the buffer for port 80, designated for web services. The server then formulates a reply, which reverses the source and destination information. All packets exchanged during this session will carry the same identifying information, allowing devices such as routers and firewalls to recognize that they belong to the same conversation.

## URI, URN, and URL
Web resources and web services such as RESTful APIs are identified using a Uniform Resource Identifier (URI). A URI is a string of characters that identifies a specific network resource. As shown in the figure, a URI has two specializations:

Uniform Resource Name (URN) - This identifies only the namespace of the resource (web page, document, image, etc.) without reference to the protocol.
Uniform Resource Locator (URL) - This defines the network location of a specific resource on the network. HTTP or HTTPS URLs are typically used with web browsers. Other protocols such as FTP, SFTP, SSH, and others can be used as a URL. A URL using SFTP might look like: sftp://sftp.example.com.
These are the parts of a URI:

Protocol/scheme - HTTPS or other protocols such as FTP, SFTP, mailto, and NNTP
Hostname - w​ww.example.com
Path and file name - /author/book.html
Fragment - #page155

**https://www.example.com/author/book.html#page155**

**URI**: https://www.example.com/author/book.html#page155
**URL**: https://www.example.com/author/book.html
**URN**: www.example.com/author/book.html
**FRAGMENT**: #page155

## NETWORK APPLICATION SERVICES
The most common internet services that people use regularly include:

**Internet Searches**: Services like Google, Bing, and Yahoo! allow users to find information on various topics through search engines.
**Social Media Sites**: Platforms such as Facebook, Twitter, Instagram, and LinkedIn enable users to connect, share, and communicate with others.
**Video Streaming**: Services like YouTube, Netflix, Hulu, and Amazon Prime Video allow users to watch movies, TV shows, and other video content on demand.
**Audio Streaming**: Music services like Spotify, Apple Music, and SoundCloud provide access to a vast library of songs and audio content for streaming.
**Online Shopping**: E-commerce sites such as Amazon, eBay, and Walmart allow users to browse and purchase products online.
**Email**: Email services like Gmail, Outlook, and Yahoo Mail facilitate sending and receiving messages and attachments over the internet.
**Messaging**: Instant messaging apps such as WhatsApp, Slack, and Telegram enable real-time communication through text, voice, and video.

Protocols Involved
Each of these services relies on protocols from the TCP/IP protocol suite to ensure reliable communication between clients and servers. Some key protocols include:

**DNS (Domain Name System)**: Resolves domain names into IP addresses for web access.
**SSH (Secure Shell)**: Provides secure remote login and command execution.
**DHCP (Dynamic Host Configuration Protocol)**: Automatically assigns IP addresses and network configurations.
**FTP (File Transfer Protocol)**: Transfers files between client and server.
**HTTP/HTTPS (Hypertext Transfer Protocol/Secure)**: Communicates web pages; HTTPS adds encryption for security.
**SMTP (Simple Mail Transfer Protocol)v: Sends emails between clients and servers.
**POP3/IMAP (Post Office Protocol 3/Internet Message Access Protocol)**: Retrieves and manages emails from a mail server; IMAP supports synchronization across devices.
**TCP/UDP (Transmission Control Protocol/User Datagram Protocol)**: TCP ensures reliable, ordered delivery; UDP allows for faster, connectionless communication.

These protocols ensure that data is accurately and efficiently transmitted, enabling seamless use of various internet services.

## DOMAIN NAME SYSTEM (DNS)

DNS stands for Domain Name System Server. DNS server associates a domain name or hostname with an IP address. DNS names are registered and organized on the internet within specific high-level groups, or domains. Some of the most common high-level domains on the internet are .com, .edu, and .net. When the DNS server receives the request from a host, it checks its table to determine the IP address associated with that web server. If the local DNS server does not have an entry for the requested name, it queries another DNS server within the domain.
Example: A user goes to the website www.cisco.com. The internet only understands IP addresses, not domain names.The system contacts a DNS server to find the associated IP address.

**DNS Query Process**
1- The system sends a query to the DNS server for the IP address of www.cisco.com.
2- The DNS server looks up the domain name and finds the IP address.
3- The DNS server returns the IP address to the host.
      - The host can now use the IP address to contact the web server.
      - The host can download the information to display the web page.
      
**nslookup command**
When configuring a device for network connectivity, it's important to include a DNS server address. In home networks, this is typically managed by the DHCP service on the router, which receives the DNS server address from the ISP. When you enter a website name (e.g., www.cisco.com), the DNS client on your device queries the DNS server for its corresponding IP address (e.g., 172.230.155.162) before making an HTTP request.

You can use the `nslookup` command to find the IP addresses associated with any domain name. Practice using this command in both Windows and Linux environments.

## WEB CLIENTS AND SERVERS
**HTTP (Hypertext Transfer Protocol)**: defines the rules for how information is transmitted between a client (the device requesting a web page) and a web server (the entity providing the web page). **HTML (Hypertext Markup Language)**: is the coding language used to display the content of the web page. Ittells the browser how to format the web page and what graphics and fonts to use.

The process begins when a client requests the web page at www.cisco.com. Since the internet operates using IP addresses rather than domain names, the client contacts a DNS server to resolve the domain name to its corresponding IP address. Once the IP address is obtained, the client can use HTTP to send a request to the web server at that IP address.

The web server responds by sending back the HTML code for the requested page. The client's browser then displays the web page by rendering the HTML code, allowing the user to view the content of www.cisco.com. Users can access the HTML code by selecting "View Page Source" in the browser's developer tools.
The HTTP protocol is not a secure protocol; information could easily be intercepted by other users as data is sent over the network. In order to provide security for the data, HTTP can be used with secure transport protocols. Requests for secure HTTP are sent to port 443. These requests use https in the site address in the browser, rather than http.

There are many different web servers and web clients available. The HTTP protocol and HTML standards make it possible for these servers and clients from many different manufacturers to work together seamlessly.

## FILE TRANSFER PROTOCOL (FTP)

The File Transfer Protocol (FTP) is a widely used service for transferring files over the internet. It allows users to transfer files between computers and manage them remotely through various commands like upload, download, delete, and rename.

An FTP client accesses an FTP server, initiating communication by sending control connection requests to TCP port 21. Once the session is established, data files are transferred using TCP port 20.

FTP client software is often integrated into operating systems and web browsers, while standalone FTP clients provide a user-friendly graphical interface with additional features.

## VIRTUAL TERMINALS

Telnet is one of the oldest application layer protocols in the TCP/IP suite, developed in the early 1970s to allow remote access to computer systems, similar to using directly-attached terminals. It provides a standard method for emulating text-based terminal devices over a network, enabling users to connect to servers and access their command line interfaces (CLIs) via a virtual terminal (vty) session. Telnet servers listen for client requests on TCP port 23.

After a Telnet connection is established, users can perform any authorized function on the server, just as if they were using a command line session on the server itself. If authorized, they can start and stop processes, configure the device, and even shut down the system.

Although the Telnet protocol can require a user to login, it does not support transporting encrypted data. All data exchanged during Telnet sessions is transported as plaintext across the network. This means that the data can be easily intercepted and understood.

The Secure Shell (SSH) protocol offers an alternate and secure method for server access. SSH provides the structure for secure remote login and other secure network services. It also provides stronger authentication than Telnet and supports transporting session data using encryption. As a best practice, network professionals should always use SSH in place of Telnet, whenever possible.

## EMAIL CLIENTS AND SERVERS

Email is one of the most popular client/server applications on the internet. Email servers run server software that enables them to interact with clients and with other email servers over the network.

Each mail server receives and stores mail for users who have mailboxes configured on the mail server. Each user with a mailbox must then use an email client to access the mail server and read these messages. Many internet messaging systems use a web-based client to access email. Examples of this type of client include Microsoft 365, Yahoo, and Gmail.

Mailboxes are identified by the format: user@c​ompany.domain

Various application protocols used in processing email include SMTP, POP3, and IMAP4.

**Simple Mail Transfer Protocol (SMTP)**

SMTP is used by an email client to send messages to its local email server. The local server then decides if the message is destined for a local mailbox or if the message is addressed to a mailbox on another server.
If the server has to send the message to a different server, SMTP is used between those two servers as well. 
SMTP requests are sent to port 25.

**Post Office Protocol (POP3)**

A server that supports POP clients receives and stores messages addressed to its users. When the client connects to the email server, the messages are downloaded to the client. By default, messages are not kept on the server after they have been accessed by the client. 
Clients contact POP3 servers on port 110.

**Internet Message Access Protocol (IMAP4)**

A server that supports IMAP clients also receives and stores messages addressed to its users. However, unlike POP, IMAP keeps the messages in the mailboxes on the server, unless they are deleted by the user. The most current version of IMAP is IMAP4.
IMAP4 listens for client requests on port 143

**TEXT MESSAGING**
It's one of the most popular communication tools in use today. Text messaging software is built into many online applications, smartphone apps, and social media sites.

Both clients can simultaneously send and receive messages.

Text messages may also be called instant messages, direct messages, private messages, and chat messages. Text messaging enables users to communicate or chat over the internet in real-time. Text messaging services on a computer are usually accessed through a web-based client that is integrated into a social media or information sharing site. These clients usually only connect to other users of the same site.

There are also a number of standalone text message clients such as Cisco Webex Teams, Microsoft Teams, WhatsApp, Facebook Messenger, and many others. These applications are available for a wide variety of operating systems and devices. A mobile version is typically offered. In addition to text messages, these clients support the transfer of documents, video, music, and audio files.

**INTERNET PHONE CALLS**
IP(internet phone) telephony makes use of Voice over IP (VoIP) technology, which converts analog voice signals into digital data. The voice data is encapsulated into IP packets which carry the phone call through the network.

When the IP phone software has been installed, the user selects a unique name. This is so that calls can be received from other users. 

Calls are made to other users of the same service on the internet, by selecting the username from a list. A call to a regular telephone (landline or cell phone) requires using a gateway to access the Public Switched Telephone Network (PSTN). Depending on the service, there may be charges associated with this type of call. The protocols and destination ports used by internet telephony applications can vary based on the software.
