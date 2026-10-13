# DNS Management

## 🎯 Objective
Configure and manage DNS zones and records on the domain controller, and troubleshoot common name resolution issues.

## 🧰 Environment
- Server: DC1 (DNS role installed automatically with AD DS)

## 📋 Steps

1. Reviewed the auto-created forward lookup zone
   Confirmed the AD-integrated forward lookup zone was created automatically during AD DS promotion, and reviewed the SRV records it generated for domain services.

2. Created a reverse lookup zone
   Set up a reverse lookup zone matching the lab's subnet, enabling IP-to-hostname resolution.

3. Added DNS records manually
   A record for a hostname pointing to a static IP
   PTR record for the matching reverse entry
   CNAME as an alias for an existing A record

4. Tested resolution from a client
   nslookup dc1.domain.local
   nslookup 192.168.1.10
   ping dc1.domain.local

5. Simulated and resolved a resolution failure
   Intentionally pointed a client's DNS setting to an incorrect server, observed the failure, then corrected it and confirmed resolution worked again.

6. Cleared and verified the DNS cache
   ipconfig /flushdns
   ipconfig /displaydns

## ✅ Verification / Results
- nslookup correctly resolves both forward and reverse queries
- Client successfully pings DC1 by hostname
- Deliberately broken DNS config reproduced a real "can't resolve name" failure, confirming I could diagnose the cause

## 📸 Screenshots
See screenshots/06-dns-management folder

## 🧠 What I Learned
This lab clarified why Active Directory relies specifically on SRV records to let clients locate domain controllers, and reinforced the difference between forward and reverse lookup zones. I also built a repeatable troubleshooting flow I can rely on going forward: checking ipconfig /all, then nslookup, then ping, then confirming the DNS server configuration.

## 🔗 Related Lab
Continued in Group Policy Objects (07-group-policy-objects.md)
