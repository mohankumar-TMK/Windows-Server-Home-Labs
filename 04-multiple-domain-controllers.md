# Multiple Domain Controllers & Replication

## 🎯 Objective
Add a second domain controller to the domain for redundancy, and verify that Active Directory replication is functioning correctly between both DCs.

## 🧰 Environment
- DC1: Existing domain controller (from previous labs)
- DC2: New Windows Server 2025 VM, joined to the domain and promoted to a second DC

## 📋 Steps

1. Built a second server VM (DC2)
   Installed Windows Server 2025 following the same process as the first lab, then set a static IP pointing its preferred DNS server to DC1.

2. Joined DC2 to the existing domain
   Used System Properties to join the domain as a member server first, restarted, and logged in with a domain admin account to confirm connectivity.

3. Promoted DC2 to a Domain Controller
   Installed the AD DS role, then ran the promotion wizard, selecting "Add a domain controller to an existing domain" instead of creating a new forest.

4. Verified replication
   repadmin /replsummary
   repadmin /showrepl
   dcdiag /v

5. Tested failover behavior
   Temporarily shut down DC1 and confirmed that clients could still authenticate using DC2 as the fallback domain controller.

## ✅ Verification / Results
- repadmin /replsummary showed no replication errors between DC1 and DC2
- New user created on DC1 appeared on DC2 within the expected replication interval
- Client authentication succeeded even with DC1 offline

## 📸 Screenshots
See screenshots/04-multiple-domain-controllers folder

## 🧠 What I Learned
This lab made clear why organizations run more than one domain controller — a single point of failure is a real risk, not just a theoretical concern. I also learned how AD replication actually confirms itself through repadmin output rather than just assuming it worked, and saw the distinction between joining a domain as a member server versus promoting a server to a full domain controller.

## 🔗 Related Lab
Continued in DHCP Server Configuration (05-dhcp-server-configuration.md)
