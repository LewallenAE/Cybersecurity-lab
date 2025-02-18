# 🚫 **Deny All With AppLocker Remediation** 

![Capture 1](screenshots/DenyAll/DenyAll02.png)

```powershell
<#
.SYNOPSIS
    This PowerShell script enforces a "deny-all, permit-by-exception" AppLocker policy to comply with STIG ID: WN10-00-000035.

.DESCRIPTION
    - Enables the AppLocker service if not already running.
    - Removes all existing AppLocker rules (Deny-All by default).
    - Allows only explicitly approved applications.
    - Saves the policy to C:\Windows\System32\AppLockerPolicy.xml.
    - Enforces the policy with Group Policy update.

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
    STIG-ID         : WN10-00-000035

.TESTED ON
    Date(s) Tested  : 2025-02-19
    Tested By       : Anthony Lewallen
    Systems Tested  : Windows 10
    PowerShell Ver. : 5.1+

.USAGE
    Run this script in an **elevated PowerShell session** to enforce the deny-all AppLocker policy.

    Example usage:
    PS C:\> .\STIG-WN10-00-000035.ps1 
#>

# Ensure the script is running as Administrator
$adminCheck = [System.Security.Principal.WindowsPrincipal]::new([System.Security.Principal.WindowsIdentity]::GetCurrent()).IsInRole([System.Security.Principal.WindowsBuiltInRole]::Administrator)
if (-not $adminCheck) {
    Write-Host "ERROR: This script must be run as Administrator!" -ForegroundColor Red
    Exit
}

# Define AppLocker Policy Path
$AppLockerPolicyPath = "C:\Windows\System32\AppLockerPolicy.xml"

# Step 1: Start AppLocker Service
Write-Host "`n[Step 1] Ensuring AppLocker Service is Running..."
Set-Service -Name AppIDSvc -StartupType Automatic
Start-Service -Name AppIDSvc

# Step 2: Remove any existing AppLocker rules (Deny-All by Default)
Write-Host "`n[Step 2] Removing existing AppLocker rules..."
Set-AppLockerPolicy -XmlPolicy "<AppLockerPolicy Version='1'></AppLockerPolicy>" -Clear

# Step 3: Create a new default-deny policy
Write-Host "`n[Step 3] Creating a new default-deny AppLocker policy..."
New-AppLockerPolicy -RuleType Allow -User Everyone -FileType Executable -XmlPolicy $AppLockerPolicyPath
Set-AppLockerPolicy -XmlPolicy $AppLockerPolicyPath -Merge

# Step 4: Allow Specific Trusted Applications
Write-Host "`n[Step 4] Adding allowed applications to AppLocker policy..."

$allowedApps = @(
    "C:\Program Files\*",
    "C:\Windows\System32\cmd.exe",
    "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe"
)

foreach ($app in $allowedApps) {
    Write-Host "   → Allowing: $app"
    $rule = New-AppLockerFilePathRule -Path $app -User Everyone -Action Allow
    Set-AppLockerPolicy -PolicyObject $rule -Merge
}

# Step 5: Apply Group Policy Updates
Write-Host "`n[Step 5] Enforcing AppLocker policy..."
gpupdate /force

# Step 6: Verify AppLocker Policy
Write-Host "`n[Step 6] Verifying applied AppLocker policies:"
Get-AppLockerPolicy -Effective | Format-List

Write-Host "`n✅ STIG WN10-00-000035 has been successfully applied!" -ForegroundColor Green
```
