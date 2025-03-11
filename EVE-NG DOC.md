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
  * The procedure ensures VMs are migrated from a source VMware to Proxmox VE with minimal errors or data loss, maintaining operational continuity.
  * By offering options like live-import and efficient manual methods (e.g., disk cloning), the procedure minimizes the time VMs are offline, which is critical for production-like lab environments.
  * Verification steps and post-migration tasks ensure the migrated VMs function correctly, facilitating a stable and reliable outcome.
    
## Application
This SOP applies to students, lab assistants, or IT trainees tasked with migrating VMs in a controlled environment, such as a lab or a virtualized testing setup. 
It covers both manual and automatic migration methods for VMs running Linux or Windows operating systems.

It is relevant in circumstances such as:
 * Upgrading Virtualization Platforms in a Lab Environment.
 * Replacing End-of-Life Hypervisors.
 * Testing New Virtualization Software.

## Definitions
**EVE-NG(Emulated Virtual Environment - Next Generation)** : A network emulation platform that allows users to create and test virtual network environments. It’s widely used by IT professionals for learning, training, and simulating complex network setups without physical hardware.\
**VM (Virtual Machine)** : A software-based emulation of a physical computer running an operating system and applications.\

**ESXi** : VMware’s type-1 hypervisor used as a common migration source.


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
