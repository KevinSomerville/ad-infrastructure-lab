# Setup Procedure: GPO Creation

This document covers how a Group Policy Object was created, linked to a specific OU, and verified for correct scoping in this lab.

## Steps

1. **Open Group Policy Management** on the domain controller.

2. **Create and link a new GPO.** Right-click the target OU (e.g. Sales) and select "Create a GPO in this domain, and Link it here." Give the GPO a descriptive name (e.g. Sales-Wallpaper-Policy).

3. **Edit the GPO.** Right-click the new GPO and select Edit to open the Group Policy Management Editor.

4. **Configure a setting.** Navigate to the relevant policy path and configure the desired setting. Example used in this lab:
   ```
   User Configuration > Policies > Administrative Templates > Desktop > Desktop Wallpaper
   ```

5. **Close the editor** once the setting is configured and enabled.

6. **Apply the policy on a client.** On a client machine belonging to the linked OU, run the following in Command Prompt to pull the policy immediately:
   ```
   gpupdate /force
   ```

7. **Verify the setting applied.** Log in as a user from the linked OU and confirm the configured setting took effect (e.g. wallpaper changed).

8. **Verify correct scoping.** Log in as a user from a different OU (one the GPO is not linked to) and confirm the setting did NOT apply.

9. **Confirm scoping at the policy engine level.** Run the following on the unaffected client while logged in as that user:
   ```
   gpresult /r
   ```
   Confirm the GPO does not appear under "Applied Group Policy Objects."

## Verification

- Confirmed the setting applied correctly for users in the linked OU.
- Confirmed the setting did not apply for users outside the linked OU.
- Confirmed via `gpresult /r` that the GPO was correctly scoped and not applied domain-wide.
