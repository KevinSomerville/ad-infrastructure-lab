# Setup Procedure: Account Lockout Policy

This document covers how the Account Lockout Policy was configured and tested in this lab.

## Steps

1. **Open Group Policy Management** on the domain controller.

2. **Edit the Default Domain Policy.** Account lockout policy only works reliably when set at the Default Domain Policy level, Windows applies account policies domain-wide by design and does not honor them when set on an OU-linked GPO. Right-click "Default Domain Policy" and select Edit.

3. **Navigate to the Account Lockout Policy settings:**
   ```
   Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Account Lockout Policy
   ```

4. **Set the lockout threshold.** Double-click "Account lockout threshold" and set it to 3 invalid attempts. Accept the suggested default values Windows offers for the remaining two settings, or set your own.

5. **Set lockout duration and reset counter.**
   - "Account lockout duration": 30 minutes
   - "Reset account lockout counter after": must be less than or equal to the lockout duration

6. **Apply the policy on a client.** Run the following in an elevated Command Prompt on a client VM to pull the policy immediately:
   ```
   gpupdate /force
   ```

7. **Test the lockout.** At the client login screen, enter a test user's correct username with an incorrect password 3 times in a row. On the 3rd attempt, the account locks and displays a lockout message.

8. **Unlock the account.** On the server, open Active Directory Users and Computers, right-click the locked user, go to Properties > Account tab, and check "Unlock account." Confirm the user can log in again with the correct password.

## Verification

- Confirmed the account locked after 3 failed attempts.
- Confirmed the account successfully unlocked from Active Directory Users and Computers.
- Confirmed login succeeded afterward with the correct password.
