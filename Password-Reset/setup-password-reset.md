# Setup Procedure: Password Reset

This document covers how a password reset was performed for a test user in this lab, simulating a routine Tier 1 help desk task.

## Steps

1. **Verify the user's identity.** In a real environment this would involve confirming employee ID, manager approval, or a verified email. For this lab, the test user account itself served as the identified party.

2. **Open Active Directory Users and Computers** on the domain controller.

3. **Locate the test user account** inside its Organizational Unit (e.g. Sales or IT).

4. **Reset the password.** Right-click the user account and select "Reset Password." Enter a new temporary password.

5. **Set password change requirements as needed.** Optionally check "User must change password at next logon" to require the user to set their own password on first login, this mirrors standard practice in a real environment.

6. **Confirm the reset.** Click OK to apply the new password.

7. **Test the login.** On a client machine, log in as the test user using the new temporary password and confirm access is restored.

## Verification

- Confirmed the user could log in successfully using the newly reset password.
- Confirmed the "must change password at next logon" prompt appeared where enabled.
