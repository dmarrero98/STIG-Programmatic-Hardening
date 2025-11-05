```powershell
<#
.SYNOPSIS
    This script enables a setting that prevents encrypted files from being indexed.

.NOTES
    Author          : Dillan Marrero
    LinkedIn        : linkedin.com/in/dmarrero98/
    GitHub          : github.com/dmarrero98
    Date Created    : 2025-11-05
    Last Modified   : 2025-11-05
    Version         : 1.0
    CVEs            : N/A
    Plugin IDs      : N/A
    STIG-ID         : WN11-CC-000305

.TESTED ON
    Date(s) Tested  : 2025-11-05
    Tested By       : Dillan Marrero
    Systems Tested  : 
    PowerShell Ver. : 5.1.26100.6899

.USAGE
    Put any usage instructions here.
    Example syntax:
    PS C:\> .\WN11-CC-000305.ps1 
#>

#WN11-CC-000360 
# Registry path for WinRM Client settings via Group Policy
$regPath = "HKLM:\SOFTWARE\Policies\Microsoft\Windows\WinRM\Client"

# Ensure the registry key exists
if (-not (Test-Path $regPath)) {
    New-Item -Path $regPath -Force | Out-Null
    Write-Output "Created registry key: $regPath"
}

# Set value to disallow Digest authentication
# 0 = Digest authentication disabled
Set-ItemProperty -Path $regPath -Name "AllowDigest" -Value 0 -Type DWord

Write-Output "Configured WinRM client to disallow Digest authentication"

```
