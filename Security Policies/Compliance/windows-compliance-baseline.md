# Windows Compliance Baseline

| | |
|---|---|
| **Category** | Compliance |
| **Platform** | Windows 10/11 |
| **Intune path** | Devices > Compliance > Create policy > Windows 10 and later |
| **Assigned to** | All Corporate Windows Devices (device group) |
| **Last tested** | YYYY-MM-DD |

## Purpose
Defines the minimum security state a Windows device must meet before it
is considered trusted. Devices that fall out of compliance can be blocked
from company resources through Conditional Access.

## Settings Configured
| Setting | Value | Why |
|---|---|---|
| Require BitLocker | Require | Protects data if a device is lost or stolen |
| Require Secure Boot | Require | Prevents unauthorized bootloaders and rootkits |
| Require code integrity | Require | Blocks unsigned or tampered system code |
| Minimum OS version | 10.0.19045 (adjust to current) | Ensures devices receive security patches |
| Require password to unlock | Require | Basic access control |
| Minimum password length | 12 | Resists brute-force guessing |
| Firewall | Require | Blocks unsolicited inbound traffic |
| TPM | Require | Hardware-backed key storage |
| Antivirus | Require | Confirms protection is registered and active |
| Microsoft Defender real-time protection | Require | Catches threats as they run |

## Actions for Noncompliance
| Action | Schedule |
|---|---|
| Mark device noncompliant | Immediately |
| Send email to end user | After 1 day |
| Retire noncompliant device | After 30 days (only if policy allows) |

## Assignment & Scope
Assigned to the corporate Windows device group. Test devices were placed
in a separate pilot group first. No exclusions.

## Testing
1. Enrolled a test Windows device and confirmed it showed Compliant.
2. Turned off the firewall on the device and synced.
3. Confirmed it flipped to Noncompliant and showed the failing setting
   in Device > Device compliance.
4. Re-enabled the firewall, synced, and confirmed it returned to Compliant.

## Troubleshooting Notes
- Device showed "Not evaluated" right after enrollment: waited for the
  check-in cycle, then forced a sync from Company Portal.
- (Add anything that actually happened in your lab here.)

## Screenshots
![Compliance settings](screenshots/win-compliance-settings.png)
![Noncompliant device view](screenshots/win-compliance-noncompliant.png)

## Related Policies
- [BitLocker Encryption](../Endpoint-Security/bitlocker.md)
- [Conditional Access: Require Compliant Device](../Conditional-Access/require-compliant-device.md)
