# DHCP Server Configuration

## 🎯 Objective
Install and configure the DHCP server role to automatically assign IP addresses to client machines on the lab network.

## 🧰 Environment
- Server: DC1 (Windows Server 2025)
- Client: Windows 11 test VM (set to obtain IP automatically)

## 📋 Steps

1. Installed the DHCP Server role
   Used Server Manager to add the DHCP Server role, then completed the post-install configuration wizard.

2. Authorized the DHCP server in AD
   DHCP servers must be authorized in Active Directory before they will hand out leases — done via the DHCP console.

3. Created a new scope
   Defined an IP range, subnet mask, and default gateway for the lab network.

4. Configured scope options
   Set Option 003 (Router/Gateway) and Option 006 (DNS Servers) pointing to DC1.

5. Set a reservation
   Reserved a fixed IP for a specific client's MAC address to simulate a device needing a consistent address.

6. Added an exclusion range
   Excluded a small range of IPs at the start of the scope, reserved for static-IP devices.

7. Tested from the client VM
   ipconfig /release
   ipconfig /renew
   ipconfig /all

## ✅ Verification / Results
- Client VM received an IP address within the defined scope
- Reserved client always receives the same IP on renewal
- ipconfig /all confirms DNS and gateway settings match scope options

## 📸 Screenshots
See screenshots/05-dhcp-server-configuration folder

## 🧠 What I Learned
This lab helped me understand the DORA process (Discover, Offer, Request, Acknowledge) and what actually happens on the network during an IP lease. I also learned why DHCP servers need to be authorized in Active Directory, since this prevents rogue DHCP servers from handing out incorrect addresses, and I got clearer on the practical difference between an exclusion and a reservation.

## 🔗 Related Lab
Continued in DNS Management (06-dns-management.md)
