# Windows Server 2025 Installation

## 🎯 Objective
Install and configure a Windows Server 2025 virtual machine to serve as the base environment for all subsequent labs in this repository.

## 🧰 Environment
- **Host:** Oracle VirtualBox
- **ISO:** Windows Server 2025 (evaluation)
- **VM specs:** 4GB RAM, 2 vCPU, 60GB dynamic disk

## 📋 Steps

1. **Created a new VM in VirtualBox**
   Configured the VM type as Windows Server, allocated RAM and disk resources appropriate for running AD DS and related roles in later labs.

2. **Attached the Windows Server 2025 ISO**
   Mounted the ISO to the virtual optical drive and set it as the primary boot device.

3. **Ran through Windows Setup**
   Selected language and region, chose the Desktop Experience install option, accepted the license terms, and completed a custom installation to the virtual disk.

4. **Set the local Administrator password**
   Completed initial setup and configured a strong local administrator password.

5. **Installed VirtualBox Guest Additions**
   Improved display resolution and enabled clipboard sharing between host and guest for a smoother lab workflow.

6. **Verified the installation**
   Confirmed the server booted correctly and reviewed system details using:
