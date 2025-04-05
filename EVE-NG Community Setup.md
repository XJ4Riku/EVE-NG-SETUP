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

[More informations from EVE-NG community Cookbook](https://www.eve-ng.net/index.php/documentation/community-cookbook/)

## Download EVE-NG
* Go to the official [EVE-NG website](https://www.eve-ng.net/)
* Navigate to the "Downloads" section.
* After selecting the Community Edition, you’ll be directed to the download page.
* You’ll see options for different virtualization platforms, including:
  1. ISO file  For bare-metal installation or custom VM setup 
  2. OVA file  Pre-configured virtual machine image for VMware or VirtualBox 
### * For this guide, we’ll use the ISO file to install EVE-NG on VMware Workstation.

## Installation Steps
1. Prepare VMware Workstation
Ensure VMware Workstation is installed on your system. [VMWare website](https://support.broadcom.com/group/ecx/productdownloads?subfamily=VMware+Workstation+Pro)
2. Create a New Virtual Machine
   1. Open VMware Workstation and go to the homepage.
   2. Click "Create a New Virtual Machine" and select "Typical (recommended)" to proceed.
   3. In the "Install Source" section, choose "Installer disc image file (iso)" and browse to select the EVE-NG ISO file you downloaded (EVE-NG is based on a 64-bit Ubuntu OS).
   4. Name your virtual machine (e.g., "EVE-NG") and specify a location for the VM files if needed.
   5. Set the virtual disk size (e.g., 50 GB). Choose whether to store the virtual disk as a single file or split it into multiple files.
3. Configure Virtual Machine Settings
   1. Before starting the VM, click "Customize Hardware" to adjust the settings:
   2. Memory: Allocate at least 8 GB (more if possible).
   3. Processors: Assign 4 cores or more.
   4. Network Adapter: Set to "NAT" or "Bridged" depending on your needs.
   5. CD/DVD: Ensure it’s connected to the EVE-NG ISO file.
   6. Save the settings and click "Finish."
5. Install EVE-NG
   1. Power on the virtual machine.
   2. You’ll see two options. Select "Install EVE-NG Community 6.2.0-4" and press Enter.
   3. In the "Keyboard configuration" screen, choose your keyboard layout (e.g., English US) and click "Done."
   4. Skip the network configuration prompt by clicking "Continue" (you can configure it later).
   5. The installation will proceed automatically. Take a break and grab a coffee—this may take a few minutes.
   6. After installation, the VM will reboot. You might see an error like [FAILED] Failed unmounting /cdrom. Don’t worry; it’s just because the ISO isn’t mounted at boot.
7. Initial Setup
   1. After rebooting, log in with the default credentials:
      ```
      Username: root
      Password: eve
      ```
   2. The first login will prompt you to change the password. Enter a new password twice (or reuse eve if you’re worried about forgetting it).
   3. Configure the network:
      1. Run ifconfig to check the network interface (e.g., eth0).
      2. Edit the network configuration file with: nano /etc/netplan/01-netcfg.yaml
      3. Example configuration:
        ```
        network:
         version: 2
          ethernets:
            eth0:
              dhcp4: true
        ```
   4. Save the file (Ctrl+O, Enter, Ctrl+X) and apply changes with: netplan apply
   5. Verify connectivity by pinging an external site: ping www.google.com
6. Access EVE-NG Web Interface
   * Open a browser on your host machine and enter the IP address of the EVE-NG VM (found via ifconfig).
   * Log in with:
   ```
   Username: admin
   Password: eve
   ```
7. Adding Device Images
   * EVE-NG doesn’t come with pre-installed device images due to licensing restrictions. You’ll need to source and upload images yourself (e.g., Cisco IOS, Juniper, etc.).
   * Here’s how:
     1. Obtain Images: Legally acquire device images from vendors or authorized sources.
     2. Upload Images: Use an SFTP client (e.g., WinSCP) to connect to the EVE-NG VM (IP address, root credentials).
     3. Navigate to /opt/unetlab/addons/qemu/.
     4. Create a folder for your image (e.g., cisco-ios-15.2).
     5. Upload the image file (e.g., .qcow2 format).
   * Fix Permissions: On the EVE-NG VM, run:
   ```
   /opt/unetlab/wrappers/unl_wrapper -a fixpermissions
   ```
   * The uploaded image will now be available in the EVE-NG web interface under "Add Node."

## Creating Your First Lab
1. In the EVE-NG web interface, click "Lab" > "New Lab."
2. Name your lab (e.g., "Test Lab") and click "Save."
3. Add devices:
   * Click "Add an object" > "Node."
   * Select a device type (e.g., Cisco IOS) and configure its settings (CPU, RAM, etc.).
4. Connect devices:
   * Click "Add an object" > "Network" to create a network segment.
   * Drag connections between device interfaces.
5. Start the lab:
   * Right-click each node and select "Start."
   * Access device consoles via the web interface (HTML5 or Telnet).

## Conclusion
With EVE-NG installed, you now have a fully functional network lab at your fingertips. Whether you’re studying for certifications or testing network designs, EVE-NG offers a robust platform to hone your skills. Start exploring and building your virtual networks today!
