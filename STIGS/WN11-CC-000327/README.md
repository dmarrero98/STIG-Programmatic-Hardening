```powershell
<#
.SYNOPSIS
    Enables PowerShell transcription for all users to record executed commands for auditing and forensic purposes.

.NOTES
    Author          : Dillan Marrero
    LinkedIn        : linkedin.com/in/dmarrero98/
    GitHub          : github.com/dmarrero98
    Date Created    : 2025-11-05
    Last Modified   : 2025-11-05
    Version         : 1.0
    CVEs            : N/A
    Plugin IDs      : N/A
    STIG-ID         : WN11-CC-000327

.TESTED ON
    Date(s) Tested  : 2025-11-03
    Tested By       : Dillan Marrero
    Systems Tested  : 
    PowerShell Ver. : 5.1.26100.6899

.USAGE
    Put any usage instructions here.
    Example syntax:
    PS C:\> .\WN11-CC-000327.ps1 
#>


# Define the transcription directory path
$transcriptionPath = "C:\PowerShell\Transcription"

# Check if the directory exists; if not, create it
if (-Not (Test-Path -Path $transcriptionPath)) {
    New-Item -ItemType Directory -Path $transcriptionPath -Force
    Write-Output "Created transcription directory at $transcriptionPath"
} else {
    Write-Output "Transcription directory already exists at $transcriptionPath"
}

# Enable PowerShell transcription for all users via registry
$regPath = "HKLM:\Software\Policies\Microsoft\Windows\PowerShell\Transcription"
if (-Not (Test-Path $regPath)) {
    New-Item -Path $regPath -Force
    Write-Output "Created registry path for PowerShell transcription."
}

# Set transcription settings
Set-ItemProperty -Path $regPath -Name "EnableTranscripting" -Value 1 -Type DWord
Set-ItemProperty -Path $regPath -Name "OutputDirectory" -Value $transcriptionPath -Type String

Write-Output "PowerShell transcription enabled. All transcripts will be saved to $transcriptionPath"
```
