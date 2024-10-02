## CLOUD AND CLOUD SERVICES

**Cloud and Virtualization**

In cloud computing, three main components are discussed: data centers, cloud services, and virtualization. Data centers are typically large facilities that provide substantial power, cooling, and bandwidth, often managed by large organizations like Facebook or Google. Smaller organizations may lease space from these data centers. Cloud service providers, such as Cisco, Amazon Web Services, and Microsoft Azure, operate out of these centers.

There are two types of clouds: public clouds, which offer services to the general public, and private clouds, intended for specific organizations, such as government entities, with restricted access.

Cloud services are categorized into three main types:

SaaS (Software as a Service): On-demand software available through a subscription model, such as Office 365 and Adobe Creative Cloud. Users typically lease access to the software.
PaaS (Platform as a Service): Provides a platform for developers to build applications, often including databases and development tools.
IaaS (Infrastructure as a Service): Offers virtual computing resources over the internet, including virtual servers and storage, on an as-needed basis.
Virtualization separates the operating system from physical hardware, allowing multiple virtual computers to run on a single physical machine. This is achieved through a hypervisor, which can be either a Type 1 (bare metal) hypervisor, installed directly on hardware, or a Type 2 (hosted) hypervisor, which runs on top of an existing operating system. Examples of Type 1 hypervisors include KVM, VMware ESXi, and Microsoft Hyper-V, while Type 2 hypervisors include VirtualBox and VMware Workstation.

Virtualization also extends to networking, where virtual switches, like the Cisco Nexus 1000V, enable network connectivity in virtual environments.

**Types of Clouds**

There are four primary cloud models:

Public clouds - Cloud-based applications and services offered in a public cloud are made available to the general population. Services may be free or are offered on a pay-per-use model, such as paying for online storage. The public cloud uses the internet to provide services.

Private clouds - Cloud-based applications and services offered in a private cloud are intended for a specific organization or entity, such as the government. A private cloud can be set up using the private network of an organization, though this can be expensive to build and maintain. A private cloud can also be managed by an outside organization with strict access security.

Hybrid clouds - A hybrid cloud is made up of two or more clouds (example: part private, part public), where each part remains a separate object, but both are connected using a single architecture. Individuals on a hybrid cloud would be able to have degrees of access to various services based on user access rights.

Community clouds - A community cloud is created for exclusive use by a specific community. The differences between public clouds and community clouds are the functional needs that have been customized for the community. For example, healthcare organizations must remain compliant with policies and laws (e.g., HIPAA) that require special authentication and confidentiality.

**Cloud computing and virtualization**

While cloud computing and virtualization are often used interchangeably, they are distinct concepts, with virtualization serving as the foundation for cloud computing. Over a decade ago, VMware pioneered a virtualization technology that allows a host operating system to support multiple client operating systems, which has since become a standard in data centers and enterprise networks.

Virtualization refers to creating virtual versions of resources, such as running a Linux environment on a Windows PC. Historically, enterprise servers operated with a dedicated server operating system installed on specific hardware, where all resources like RAM, processing power, and storage were exclusively allocated to that server's services (e.g., web or email).

This setup led to significant issues:

SINGLE POINT OF FAILURE: If a component failed, the entire service became unavailable.

SERVER SPRAWL: Dedicated servers often remained idle, wasting energy and space, leading to inefficient resource utilization.

## VIRTUALIZATION


