# Active Directory Account Creation, Cmd Commands

## 🎯 Objective
Create and manage user accounts in Active Directory, and practice common Cmd/PowerShell commands used for day-to-day AD administration.

## 🧰 Environment
- Server: DC1 (Windows Server 2025, domain controller from previous lab)
- Tool: Active Directory Users and Computers (ADUC)

## 📋 Steps

1. Created Organizational Units (OUs)
   Set up OUs to organize accounts logically (e.g. Sales, IT, HR) instead of placing everyone in the default Users container.

2. Created individual user accounts
   Used ADUC to create new users within the correct OU, filled in first/last name and logon name, and set a temporary password with "User must change password at next logon" checked.

3. Copied an existing user
   Used the Copy feature on an existing account to quickly create a new user with the same group memberships and OU placement — a common shortcut for onboarding similar roles.

4. Practiced common Cmd/PowerShell commands
   net user
   net user username /domain
   whoami /groups
   ipconfig /all
   nltest /dsgetdc:domain.local

5. Verified account creation
   Logged into a client VM with a newly created domain account to confirm authentication worked.

## ✅ Verification / Results
- New users visible in ADUC under correct OUs
- Domain login succeeded from client VM
- net user /domain correctly returned account details

## 📸 Screenshots
See screenshots/03-ad-user-account-creation folder

## 🧠 What I Learned
This lab showed me why OU structure matters for applying Group Policy later — labs are easier to manage when accounts aren't all in one bucket. I also got a clearer sense of the practical difference between local account management (net user) and domain-level account management, and saw how the Copy User feature saves time for onboarding while also learning what it does and doesn't carry over.

## 🔗 Related Lab
Continued in Multiple Domain Controllers & Replication (04-multiple-domain-controllers.md)
