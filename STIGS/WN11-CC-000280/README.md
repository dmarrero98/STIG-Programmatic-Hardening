```powershell
<#
.SYNOPSIS
    This script enables incoming RDP connections to always prompt for password input

.NOTES
    Author          : Dillan Marrero
    LinkedIn        : linkedin.com/in/dmarrero98/
    GitHub          : github.com/dmarrero98
    Date Created    : 2025-11-05
    Last Modified   : 2025-11-05
    Version         : 1.0
    CVEs            : N/A
    Plugin IDs      : N/A
    STIG-ID         : WN11-CC-000280

.TESTED ON
    Date(s) Tested  : 2025-11-03
    Tested By       : Dillan Marrero
    Systems Tested  : 
    PowerShell Ver. : 5.1.26100.6899

.USAGE
    Example syntax:
    PS C:\> .\WN11-CC-000280.ps1 
#>

#WN11-CC-000280
# Registry path for Remote Desktop "Always prompt for password"
$regPath = "HKLM:\SOFTWARE\Policies\Microsoft\Windows NT\Terminal Services"

# Ensure the registry path exists
if (-not (Test-Path $regPath)) {
    New-Item -Path $regPath -Force | Out-Null
    Write-Output "Created registry path for Terminal Services."
}

# Set the value to enforce "Always prompt for password"
Set-ItemProperty -Path $regPath -Name "fPromptForPassword" -Value 1 -Type DWord

Write-Output "Remote Desktop is now configured to always prompt for passwords upon connection."


```
