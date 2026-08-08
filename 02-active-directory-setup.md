# Rename Server & Install Active Directory

## 🎯 Objective
Rename the server and install Active Directory Domain Services (AD DS) to establish a new domain, turning the server into a domain controller.

## 🧰 Environment
- **Host:** Oracle VirtualBox
- **VM:** Windows Server 2025 (from previous lab)
- **Server Name:** DC1
- **Domain Name:** chit1.local

## 📋 Steps

1. **Renamed the server**
   Renamed the default server hostname to `DC1` via Server Manager → Local Server, then restarted to apply the change.

2. **Installed the AD DS role**
   Used the *Add Roles and Features Wizard* to install Active Directory Domain Services and its management tools.

3. **Promoted the server to a Domain Controller**
   Ran the post-deployment configuration to create a new forest, set the root domain name, and configured the Directory Services Restore Mode (DSRM) password.

4. **Verified installation**
   Confirmed the domain was active using:
   ```powershell
   Get-ADDomain
   dcdiag /v
