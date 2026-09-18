# ad-infrastructure-lab
This is a self-hosted Active Directory lab for practicing core domain administration tasks, including user provisioning, password resets, account unlocks, and group policy enforcement.

# Overview
I built a Windows Server-based Active Directory Lab with Windows Server 2025 and 3 Windows 11 Enterprise virtual machines. I used Oracle VirtualBox (Version 7.2.16) as the hypervisor and configured an internal network to enable VM-to-VM connectivity. I will showcase critical skills within Active Directory: Networking Fundamentals, password reset/account unlock, and Group Policy enforcement.

# OS used
- Windows Server 2025
- Windows 11 Enterprise x3

# Setup Procedures
  * Download an image of Windows Server(2019-2025) and Windows Enterprise(10/11) from the official Windows website

  *  Create 1 Windows Server 2025 VM and 3 Windows 11 Enterprise VM

  * Set all virtual machine adapter 1 to the Internal network for VM-to-VM connectivity

  *   Install Windows Server on the Server 2025 VM using the standard setup wizard. Set a static IP address on it once installed (Control Panel > Network Settings), since a domain controller needs a fixed address.

  *   In Server Manager, click 'Add Roles and Features,' select 'Active Directory Domain Services,' and complete the wizard. Once installed, promote the server to a domain controller and create a new forest (e.g. lab.local).

  *   Set the client's DNS server to point to your domain controller's static IP. On the client VM, go to System Properties > Change domain, enter your domain name (lab.local), and provide domain admin credentials when prompted. Restart when asked. Confirm the machine now shows as joined in Active Directory Users and Computers on the server.
