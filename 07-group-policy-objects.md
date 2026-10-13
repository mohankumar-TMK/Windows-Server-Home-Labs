# Group Policy Objects (GPOs)

## 🎯 Objective
Create and link Group Policy Objects to enforce settings across users and computers in the domain, and confirm they apply correctly on a client.

## 🧰 Environment
- Server: DC1 (Group Policy Management Console)
- Client: Windows 11 VM, domain-joined, member of a test OU

## 📋 Steps

1. Opened Group Policy Management Console (GPMC)
   Reviewed the default Domain Policy and Default Domain Controllers Policy already in place.

2. Created a new GPO
   Created and linked a new GPO to the target OU, naming it clearly to reflect its purpose.

3. Configured a password policy
   Set minimum password length, complexity requirements, and account lockout threshold under the Account Policies security settings.

4. Configured a basic login script / desktop setting
   Set a simple policy to verify user-level policy application, not just security settings.

5. Linked the GPO to the correct OU
   Confirmed the GPO was scoped only to the intended OU, not the entire domain.

6. Forced policy update on the client
   gpupdate /force
   gpresult /r

7. Verified enforcement
   Attempted to set a weak password on a test account in the linked OU to confirm the policy rejected it.

## ✅ Verification / Results
- gpresult /r shows the new GPO applied under Applied Group Policy Objects
- Weak password attempt was rejected, confirming the policy took effect
- Accounts outside the linked OU were unaffected, confirming correct scoping

## 📸 Screenshots
See screenshots/07-group-policy-objects folder

## 🧠 What I Learned
This lab taught me that GPOs apply based on exactly where they're linked (OU, domain, or site), and that scoping mistakes can affect the wrong accounts. gpupdate /force and gpresult /r are two commands I expect to use constantly going forward to test and confirm policy application, and I also got a better sense of how precedence works when multiple GPOs could apply to the same object.

## 🔗 Related Lab
Continued in NTFS Permissions & File Sharing (08-ntfs-permissions-file-sharing.md)
