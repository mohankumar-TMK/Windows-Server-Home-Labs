# PowerShell Automation

## 🎯 Objective
Use PowerShell to automate repetitive AD administration tasks, specifically bulk user creation from a CSV file and a basic system health check script.

## 🧰 Environment
- Server: DC1
- Tool: PowerShell ISE / PowerShell 7, Active Directory module

## 📋 Steps

1. Prepared a CSV of sample users
   Created a CSV file with columns for first name, last name, username, OU, and password.

2. Wrote a bulk user creation script
   Used Import-Csv combined with New-ADUser in a loop to create multiple accounts from the CSV in one run.

3. Ran and verified the script
   Executed the script, then confirmed all users appeared correctly in ADUC under their target OUs.

4. Wrote a basic system monitoring script
   Used Get-Service to check for stopped automatic services, Get-Counter to check available memory, and Get-EventLog to review recent system errors.

5. Combined into a simple daily-check script
   Wrote a script that runs both the stopped-services check and recent system errors check, and outputs results to a text file with a timestamp.

## ✅ Verification / Results
- Test users created correctly from CSV with matching OU placement
- Monitoring script correctly flagged a manually stopped automatic service during testing
- Output file generated with timestamp confirms the script ran unattended

## 📸 Screenshots
See screenshots/09-powershell-automation folder

## 🧠 What I Learned
This lab showed me how much better bulk operations via CSV and Import-Csv scale compared to manual entry in ADUC, which matters for realistic scenarios like onboarding a batch of new hires. I also learned that a lot of basic system monitoring can be done with native PowerShell cmdlets like Get-Service, Get-Counter, and Get-EventLog without needing third-party tools, and that writing scripts with parameters instead of hardcoded values makes them far more reusable.

## 🔗 Related Lab
This concludes the current lab series. Future labs will build on this environment.
