## RELIABLE NETWORKS

**Network architecture**

Networks have evolved from simple data systems to complex environments that connect people, devices, and information. To ensure efficient operation, networks are built on standard architectures that include physical infrastructure and protocols for moving data. 
These four characteristics are:

- Fault Tolerance
  
- Scalability

- Quality of Service (QoS)

- Security

**Fault tolerance**

A fault tolerant network is one that can continue operations without interruption when one or more components of the network fail. Installing additional links into the network giving multiple paths to reach the ISP and the internet is known as redundancy, 
one of the ways to make the network fault tolerant.

A packet-switched network ensures reliability by providing redundancy. It breaks data, like emails or video streams, into smaller packets, each containing source and destination information. 
These packets are routed through the network based on current conditions, meaning they may take different paths to reach the same destination. 
This method helps maintain efficient communication even if parts of the network experience issues.

**Scalability**

A scalable network expands quickly to support new users and applications. It does this without degrading the performance of services that are being accessed by existing users. The figure shows how a new network is easily added to an existing network. 
These networks are scalable because the designers follow accepted standards and protocols.

**Quality of Service (QoS)**

Quality of Service (QoS) is crucial for modern networks due to increasing demands from applications like voice and live video. QoS helps manage network congestion by prioritizing time-sensitive traffic, such as voice, over less critical data like web browsing. 
Congestion occurs when the demand for bandwidth exceeds what’s available. Bandwidth is the amount of data that can be transmitted in a second, measured in bits per second (bps). When bandwidth is limited, devices hold packets in memory until space is available. 
QoS policies ensure essential traffic, like voice, gets priority to maintain service quality during congestion.

**Network Security**

The network infrastructure, services, and the data contained on network-attached devices are crucial personal and business assets. Network administrators must address two types of network security concerns: network infrastructure security and information security.

Securing the network infrastructure includes physically securing devices that provide network connectivity and preventing unauthorized access to the management software that resides on them, as shown in the figure.
Network administrators must also protect the information contained within the packets being transmitted over the network, and the information stored on network attached devices. 
In order to achieve the goals of network security, there are three primary requirements:

**Confidentiality** - Data confidentiality means that only the intended and authorized recipients can access and read data.

**Integrity** - Data integrity assures users that the information has not been altered in transmission, from origin to destination.

**Availability** - Data availability assures users of timely and reliable access to data services for authorized users.

## HIERARCHICAL NETWORK DESIGN

In an Ethernet network, the MAC address uniquely identifies a host, similar to a person's name, but it doesn't show the host's location. Relying solely on MAC addresses for millions of devices would make finding one very difficult. Additionally, Ethernet generates a lot of broadcast traffic, which slows down performance. 
If all internet hosts were on one Ethernet network, this broadcast traffic would overwhelm the system. To improve efficiency, large networks are divided into smaller, manageable parts using a hierarchical design model.
Both the physical MAC and logical IP addresses are required for a computer to communicate on a hierarchical network.

**Benefits of a Hierarchical Network Design**

A hierarchical network design is beneficial for scaling networks efficiently, especially as they grow beyond basic setups. 
While home networks may grow organically by adding devices like computers or printers, this approach can lead to inefficiencies in larger networks. 
In businesses, critical devices like servers might end up sharing space with non-essential traffic, causing interference and slowdowns.

Hierarchical design solves this by organizing networks into three layers:

**Access layer**: 

The access layer connects end-user devices, like computers or phones, to the network. 
It uses network devices like switches (e.g., Cisco 2960-XR) or wireless access points to allow multiple hosts to communicate. Devices in the access layer typically share the same network portion of their IP addresses. 
If a message is destined for a local host, it stays within the access layer; if it's for another network, it is passed to the distribution layer.

**Distribution layer**: 

The distribution layer connects separate networks and controls the flow of traffic between them. 
It uses more powerful switches (e.g., Cisco C9300 series) and routers to manage traffic between networks. 
This layer ensures that the type and amount of traffic from the access layer is efficiently routed to the core layer, providing a critical point for managing inter-network communication and traffic control.

**Core layer**: The core layer serves as the high-speed backbone of the network, transporting large volumes of data between multiple networks. 
It uses highly powerful and fast devices, such as Cisco Catalyst 9600 switches and routers, and provides redundant connections to ensure reliability. 
The primary goal of the core layer is to transport data quickly and efficiently across the network.

By planning networks using this structure, traffic is efficiently managed, critical systems are protected, and the network can scale without causing unnecessary congestion or failures.
