#  EVE-NG Community Edition Setup
![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTfl4UoFvHn9M4mdhpcJL_uAXgQ4WHNLbVNRkBRS8V0LDq0jITBZC12xwXaYbQ1TzTOOD8&usqp=CAU)

[MITT NSA](https://mitt.ca/programs/post-secondary-programs/2385/network-and-systems-administrator-diploma) Winter 24P2\
130 Henlow Bay, Winnipeg, MB R3Y 1G4\
(204) 989-6500\
*Version #1 of document*\
Written by:  **Ching-An Hu** **Ching-Chuan Hu**\
Approved by: **Victor Chavez**\
Date: 03/11/2025

## Purpose
This Standard Operating Procedure (SOP) is designed  to provide a clear and repeatable process for installing **EVE-NG community edition**, loading **Device Image**, fixing **PHP Warning**, and creating **Lab**. 
This ensures proper configuration, and compatibility with the target system while maintaining best practices for academic or lab environments.

The procedure aims to facilitate:
  * The procedure ensures setup and configuration of virtual network labs in EVE-NG, enabling users to efficiently emulate complex network topologies for testing and training purposes
  
    
## Application
This SOP applies to students, lab assistants, or IT trainees using EVE-NG for hands-on learning, certification prep (e.g., CCNA), safe experimentation, multi-vendor exposure, collaborative labs, applying theory (e.g., VLANs), cost-effective practice, intro to automation, real-world scenarios, and guided troubleshooting in a virtual network environment.

It is relevant in circumstances such as:
 * Converting from Cisco Packet Tracer to EVE-NG environment for more advanced emulation and multi-vendor support.
 * Transitioning from theoretical study to practical, scalable network simulations.
 * Conducting group labs where physical hardware is limited or unavailable.
 * Preparing for real-world scenarios by simulating enterprise-grade network setups.
 * Practicing automation and scripting in a controlled, virtualized environment.

## Definitions
**EVE-NG(Emulated Virtual Environment - Next Generation)** : A network emulation platform that allows users to create and test virtual network environments. It’s widely used by IT professionals for learning, training, and simulating complex network setups without physical hardware.\
**VM (Virtual Machine)** : A software-based emulation of a physical computer running an operating system and applications.\
**CISCO** : An American multinational digital communications technology conglomerate corporation.\
**Packet Tracer** : A computer networking simulation software for teaching and learning networking, IoT, and cybersecurity skills in a virtual lab.\
**WinSCP** : An open source free SFTP client, FTP client, WebDAV client, S3 client and SCP client and file manager for Windows.\
**Filezilla** : A free, open source FTP client supports FTP, SFTP, and FTPS (FTP over SSL/TLS) is available on Windows, Linux and Mac OS X.


## Hardware requirements for EVE-NG
### Minimal Laptop/PC Desktop system requirements
<table>
    <tr>
        <th colspan="2">PC/Laptop HW requirements</th>
    </tr>
    <tr>
        <td>CPU</td>
        <td>Intel i7 (8 Logical processors vCPU), Enabled Intel virtualization in BIOS</td>
    </tr>
    <tr>
        <td>RAM</td>
        <td>8GB</td>
    </tr>
    <tr>
        <td>HDD Space</td>
        <td>50GB</td>
    </tr>
    <tr>
        <td>Network</td>
        <td>LAN/WLAN</td>
    </tr>
    <tr>
        <th colspan="2">EVE Virtual machine requirements</th>
    </tr>
    <tr>
        <td>CPU</td>
        <td>1/8 (Amount of processors/Number of cores per processor) Enabled Virtualize Intel VT-x/EPT or AMD-V/RVI and virtualize IOMMU options</td>
    </tr>
    <tr>
        <td>RAM</td>
        <td>8GB or more</td>
    </tr>
    <tr>
        <td>HDD</td>
        <td>50GB or more</td>
    </tr>
    <tr>
        <td>Network</td>
        <td>VMware NAT or Bridged network adapter</td>
    </tr>
</table>

[More informations from EVE-NG community Cookbook](https://www.eve-ng.net/index.php/documentation/community-cookbook/))
