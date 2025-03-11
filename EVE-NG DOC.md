#  Migrate VMware machine to Proxmox VE 
![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTfl4UoFvHn9M4mdhpcJL_uAXgQ4WHNLbVNRkBRS8V0LDq0jITBZC12xwXaYbQ1TzTOOD8&usqp=CAU)

[MITT NSA](https://mitt.ca/programs/post-secondary-programs/2385/network-and-systems-administrator-diploma) Winter 24P2\
130 Henlow Bay, Winnipeg, MB R3Y 1G4\
(204) 989-6500\
*Version #1 of document*\
Written by:  **Ching-An Hu** **Ching-Chuan Hu**\
Approved by: **Rogelio Villaver Jr**\
Date: 03/05/2025

## Purpose
This Standard Operating Procedure (SOP) is designed  to provide a clear and repeatable process for migrating **Virtual Machines (VMs)** from an existing **VMware ESXi** or **local VMware** to **Proxmox Virtual Environment (VE)**. 
This ensures minimal downtime, proper configuration, and compatibility with the target system while maintaining best practices for academic or lab environments.

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
**VM (Virtual Machine)** : A software-based emulation of a physical computer running an operating system and applications.\
**Proxmox VE** : An open-source virtualization platform based on QEMU/KVM and LXC.\
**Hypervisor** : Software that creates and manages VMs (e.g., VMware ESXi or Proxmox VE).\
**VirtIO** : Paravirtualized drivers that improve VM performance on compatible systems.\
**Live-Import** : A migration method that starts the VM during the import process to reduce downtime.\
**OVF/OVA** : Open Virtualization Format, a standard for packaging and distributing VMs.\
**ESXi** : VMware’s type-1 hypervisor used as a common migration source.


## Hardware requirements for Proxmox Virtual Environment
|Components     |Minimum Requirements    |
|---------------|------------------------|
|CPU            |Intel 64 or AMD64 with Intel VT/AMD-V CPU flag. | 
|RAM            |Minimum 2 GB for OS and Proxmox VE services. Plus designated memory for guests. For Ceph or ZFS additional memory is required, approximately 1 GB memory for every TB used storage. |
|OS Storage        |Fast and redundant storage, best results with SSD disks. Hardware RAID with batteries protected write cache (“BBU”) or non-RAID with ZFS and SSD cache.|
|VM Storage        |For local storage use a hardware RAID with battery backed write cache (BBU) or non-RAID for ZFS. Neither ZFS nor Ceph are compatible with a hardware RAID controller. Shared and distributed storage is also possible.|
|Network        |Redundant Gbit NICs, additional NICs depending on the preferred storage technology and cluster setup – 10 Gbit and higher is also supported. |
|Connect|For PCI(e) passthrough a CPU with VT-d/AMD-d CPU flag is needed.|

[More informations from Proxmox offical website](https://www.proxmox.com/en/products/proxmox-virtual-environment/requirements).
