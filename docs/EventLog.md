# **Changing The Event Log Size To 32768KB Or Greater**


### **Implemented Code**

![Capture 1](screenshots/EventLog/01.png)
![Capture 2](screenshots/EventLog/02.png)


```powershell
<#
.SYNOPSIS
    This PowerShell script configures the Application event log size to at least 32768 KB to comply with STIG ID: WN10-AU-000500.

.DESCRIPTION
    - Ensures the Application event log size is set to 32768 KB or greater.
    - Modifies the event log service policy settings.
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
    STIG-ID         : WN10-AU-000500

.TESTED ON
    Date(s) Tested  : 2025-02-19
    Tested By       : Anthony Lewallen
    Systems Tested  : Windows 10
    PowerShell Ver. : 5.1+

.USAGE
    Run this script in an **elevated PowerShell session** to configure the Application event log size.

    Example usage:
    PS C:\> .\STIG-WN10-AU-000500.ps1 
#>

# Ensure the script is running as Administrator
$adminCheck = [System.Security.Principal.WindowsPrincipal]::new([System.Security.Principal.WindowsIdentity]::GetCurrent()).IsInRole([System.Security.Principal.WindowsBuiltInRole]::Administrator)
if (-not $adminCheck) {
    Write-Host "ERROR: This script must be run as Administrator!" -ForegroundColor Red
    Exit
}

# Step 1: Configure Application Event Log Size
Write-Host "`n[Step 1] Setting Application Event Log Size to 32768 KB..."
wevtutil sl Application /ms:32768

# Step 2: Apply Group Policy Updates
Write-Host "`n[Step 2] Applying Group Policy Updates..."
gpupdate /force

# Step 3: Verify the Event Log Configuration
Write-Host "`n[Step 3] Verifying the Application Event Log size..."
wevtutil gl Application | Select-String "MaxSize"

Write-Host "`n✅ STIG WN10-AU-000500 has been successfully applied!" -ForegroundColor Green
```
