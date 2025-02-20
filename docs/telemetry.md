# **Telemetry Remediation**

![Capture 1](screenshots/telemetry/01.png)


```powershell
<#
.SYNOPSIS
    This PowerShell script configures Windows Telemetry settings to comply with STIG ID: WN10-CC-000205.

.DESCRIPTION
    - Ensures Windows Telemetry is set to 'Security' (0) or 'Basic' (1).
    - Modifies the Group Policy setting for data collection.
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
    STIG-ID         : WN10-CC-000205

.TESTED ON
    Date(s) Tested  : 2025-02-19
    Tested By       : Anthony Lewallen
    Systems Tested  : Windows 10
    PowerShell Ver. : 5.1+

.USAGE
    Run this script in an **elevated PowerShell session** to configure Windows Telemetry settings.

    Example usage:
    PS C:\> .\STIG-WN10-CC-000205.ps1 
#>

# Step 1: Ensure the Registry Path Exists
Write-Host "`n[Step 1] Ensuring Registry Path Exists..."
$regPath = "HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection"
if (-not (Test-Path $regPath)) {
    Write-Host "Registry path does not exist. Creating it..." -ForegroundColor Yellow
    New-Item -Path $regPath -Force | Out-Null
}

# Step 2: Set Telemetry Level to Security (0) or Basic (1)
Write-Host "`n[Step 2] Configuring Windows Telemetry Settings..."
New-ItemProperty -Path $regPath -Name "AllowTelemetry" -Value 0 -PropertyType DWord -Force

# Step 3: Apply Group Policy Updates
Write-Host "`n[Step 3] Applying Group Policy Updates..."
gpupdate /force

# Step 4: Verify the Telemetry Policy
Write-Host "`n[Step 4] Verifying Windows Telemetry setting..."
(Get-ItemProperty -Path $regPath -Name "AllowTelemetry").AllowTelemetry

Write-Host "`n✅ STIG WN10-CC-000205 has been successfully applied!" -ForegroundColor Green
```
