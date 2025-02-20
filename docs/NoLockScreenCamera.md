# :camera: No Lock Screen Camera Remediation

### The following code turns off the ability for the camera to be turned on when the screen is locked.


![Capture 1](screenshots/NoLockScreenCamera/01.png)


```powershell
<#
.SYNOPSIS
    This PowerShell script disables camera access from the lock screen to comply with STIG ID: WN10-CC-000005.

.DESCRIPTION
    - Ensures the lock screen camera feature is disabled.
    - Modifies the Group Policy setting to prevent camera use on the lock screen.
    - Enforces the policy with a Group Policy update.

.NOTES
    Author          : Anthony Lewallen
    LinkedIn        : https://www.linkedin.com/in/anthony-lewallen
    Website         : https://lewallenae.github.io/Cybersecurity-lab/
    GitHub          : https://github.com/LewallenAE/Cybersecurity-lab
    Date Created    : 2025-02-19
    Last Modified   : 2025-02-19
    Version         : 1.0
    CVEs            : N/A
    Plugin IDs      : N/A
    STIG-ID         : WN10-CC-000005

.TESTED ON
    Date(s) Tested  : 2025-02-19
    Tested By       : Anthony Lewallen
    Systems Tested  : Windows 10
    PowerShell Ver. : 5.1+

.USAGE
    Run this script in an **elevated PowerShell session** to disable camera access from the lock screen.

    Example usage:
    PS C:\> .\STIG-WN10-CC-000005.ps1 
#>

# Step 1: Ensure the Registry Path Exists
Write-Host "`n[Step 1] Ensuring Registry Path Exists..."
$regPath = "HKLM:\SOFTWARE\Policies\Microsoft\Windows\Personalization"
if (-not (Test-Path $regPath)) {
    Write-Host "Registry path does not exist. Creating it..." -ForegroundColor Yellow
    New-Item -Path $regPath -Force | Out-Null
}

# Step 2: Disable Lock Screen Camera
Write-Host "`n[Step 2] Disabling Camera Access on Lock Screen..."
New-ItemProperty -Path $regPath -Name "NoLockScreenCamera" -Value 1 -PropertyType DWord -Force

# Step 3: Apply Group Policy Updates
Write-Host "`n[Step 3] Applying Group Policy Updates..."
gpupdate /force

# Step 4: Verify the Lock Screen Camera Policy
Write-Host "`n[Step 4] Verifying Lock Screen Camera setting..."
(Get-ItemProperty -Path $regPath -Name "NoLockScreenCamera").NoLockScreenCamera

Write-Host "`n✅ STIG WN10-CC-000005 has been successfully applied!" -ForegroundColor Green
```

