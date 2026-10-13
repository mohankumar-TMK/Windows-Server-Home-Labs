# NTFS Permissions & File Sharing

## 🎯 Objective
Configure a shared folder with both NTFS and Share permissions, and understand how the two interact when a user accesses a resource over the network.

## 🧰 Environment
- Server: DC1
- Test accounts: Two domain users with different group memberships (from earlier lab)

## 📋 Steps

1. Created a folder for sharing
   Created a shared folder on DC1 for testing permissions.

2. Set NTFS permissions
   Granted one group Modify access and another group Read-only access through the Security tab.

3. Shared the folder over the network
   Configured Share permissions separately through the Sharing tab, intentionally setting them broad to isolate NTFS as the real restriction being tested.

4. Tested access from a client
   Logged in as a member of each group separately, accessed the shared folder, and tried creating, editing, and deleting files.

5. Verified effective permissions
   Used the Effective Access tool to check what a specific user could actually do.

6. Tested permission inheritance
   Created a subfolder, confirmed it inherited the parent's NTFS permissions by default, then blocked inheritance on one test subfolder and set unique permissions.

## ✅ Verification / Results
- The Read-only group could open and read files but not save changes, confirming NTFS was the binding restriction even with broad Share permissions
- The Modify group could create, edit, and delete files as expected
- Effective Access tool matched real tested behavior

## 📸 Screenshots
See screenshots/08-ntfs-permissions-file-sharing folder

## 🧠 What I Learned
This lab made the "most restrictive permission wins" rule concrete instead of just something I had memorized — when NTFS and Share permissions differ, NTFS ended up being the deciding factor in my test. I also learned to use the Effective Access tool to predict access before testing manually, and saw why blocking inheritance should be used sparingly, since it makes permission troubleshooting harder down the line.

## 🔗 Related Lab
Continued in PowerShell Automation (09-powershell-automation.md)
