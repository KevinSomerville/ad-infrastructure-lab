# GPO Settings Summary

This document lists each Group Policy Object created in this lab, what it configures, and how it was verified.

| GPO Name | Linked OU | Setting Configured | Path in GPO Editor | Verified On |
|----------|-----------|---------------------|----------------------|-------------|
| Wallpaper-Policy | Sales | Sets a custom desktop wallpaper | User Configuration > Policies > Administrative Templates > Desktop > Desktop Wallpaper | CLIENT-01 |
| Control-Panel-Policy | IT | Disabling Control Panel access | User Configuration > Administrative Templates > Control Panel > Prohibit access to Control Panel | CLIENT-02 |
| Default Domain Policy (edited) | Domain-wide | Account lockout after 3 failed login attempts | Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Account Lockout Policy | CLIENT-03 |

## Verification Method

For each GPO, scoping was verified two ways:

1. **Visual check** - logged in as a user inside the linked OU and confirmed the setting applied (e.g. wallpaper changed). Then logged in as a user in a different OU and confirmed the setting did NOT apply.
2. **Command-line check** - ran `gpresult /r` on the client while logged in as a user outside the linked OU, and confirmed the GPO did not appear under "Applied Group Policy Objects."

## Notes

- The Account Lockout Policy was applied at the Default Domain Policy level (rather than a single OU) since lockout behavior is typically a domain-wide security setting in real environments.
- All other GPOs were scoped to a single OU to demonstrate targeted policy application rather than blanket domain-wide changes.
