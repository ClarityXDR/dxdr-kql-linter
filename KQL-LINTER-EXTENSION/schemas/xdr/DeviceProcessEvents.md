# DeviceProcessEvents

**Category:** Device Events  
**Description:** Process creation and termination events from endpoints

## Schema

| Column | Type | Description |
|--------|------|-------------|
| Timestamp | datetime | Date and time when the event was recorded |
| DeviceId | string | Unique identifier for the device |
| DeviceName | string | Fully qualified domain name (FQDN) of the device |
| ActionType | string | Type of activity that triggered the event |
| FileName | string | Name of the file that the recorded action was applied to |
| FolderPath | string | Folder containing the file that the recorded action was applied to |
| SHA1 | string | SHA-1 hash of the file that the recorded action was applied to |
| SHA256 | string | SHA-256 hash of the file that the recorded action was applied to |
| MD5 | string | MD5 hash of the file that the recorded action was applied to |
| FileSize | long | Size of the file in bytes |
| ProcessVersionInfoCompanyName | string | Company name from the version information of the process |
| ProcessVersionInfoProductName | string | Product name from the version information of the process |
| ProcessVersionInfoProductVersion | string | Product version from the version information of the process |
| ProcessVersionInfoInternalFileName | string | Internal file name from the version information of the process |
| ProcessVersionInfoOriginalFileName | string | Original file name from the version information of the process |
| ProcessVersionInfoFileDescription | string | File description from the version information of the process |
| ProcessId | int | Process ID (PID) of the newly created process |
| ProcessCommandLine | string | Command line used to create the new process |
| ProcessIntegrityLevel | string | Integrity level of the newly created process |
| ProcessTokenElevation | string | Token type indicating the presence or absence of User Access Control (UAC) privilege elevation applied to the newly created process |
| ProcessCreationTime | datetime | Date and time the process was created |
| AccountDomain | string | Domain of the account |
| AccountName | string | User name of the account |
| AccountSid | string | Security Identifier (SID) of the account |
| AccountUpn | string | User principal name (UPN) of the account |
| AccountObjectId | string | Unique identifier for the account in Azure AD |
| LogonId | long | Identifier for a logon session |
| InitiatingProcessAccountDomain | string | Domain of the account that ran the process responsible for the event |
| InitiatingProcessAccountName | string | User name of the account that ran the process responsible for the event |
| InitiatingProcessAccountSid | string | Security Identifier (SID) of the account that ran the process responsible for the event |
| InitiatingProcessAccountUpn | string | User principal name (UPN) of the account that ran the process responsible for the event |
| InitiatingProcessAccountObjectId | string | Azure AD object ID of the user account that ran the process responsible for the event |
| InitiatingProcessLogonId | long | Identifier for a logon session of the process that initiated the event |
| InitiatingProcessIntegrityLevel | string | Integrity level of the process that initiated the event |
| InitiatingProcessTokenElevation | string | Token type indicating the presence or absence of User Access Control (UAC) privilege elevation applied to the process that initiated the event |
| InitiatingProcessSHA1 | string | SHA-1 hash of the process (image file) that initiated the event |
| InitiatingProcessSHA256 | string | SHA-256 hash of the process (image file) that initiated the event |
| InitiatingProcessMD5 | string | MD5 hash of the process (image file) that initiated the event |
| InitiatingProcessFileName | string | Name of the process that initiated the event |
| InitiatingProcessFileSize | long | Size of the process (image file) that initiated the event |
| InitiatingProcessVersionInfoCompanyName | string | Company name from the version information of the process (image file) responsible for the event |
| InitiatingProcessVersionInfoProductName | string | Product name from the version information of the process (image file) responsible for the event |
| InitiatingProcessVersionInfoProductVersion | string | Product version from the version information of the process (image file) responsible for the event |
| InitiatingProcessVersionInfoInternalFileName | string | Internal file name from the version information of the process (image file) responsible for the event |
| InitiatingProcessVersionInfoOriginalFileName | string | Original file name from the version information of the process (image file) responsible for the event |
| InitiatingProcessVersionInfoFileDescription | string | File description from the version information of the process (image file) responsible for the event |
| InitiatingProcessId | int | Process ID (PID) of the process that initiated the event |
| InitiatingProcessCommandLine | string | Command line used to run the process that initiated the event |
| InitiatingProcessCreationTime | datetime | Date and time when the process that initiated the event was started |
| InitiatingProcessFolderPath | string | Folder containing the process (image file) that initiated the event |
| InitiatingProcessParentId | int | Process ID (PID) of the parent process that spawned the process responsible for the event |
| InitiatingProcessParentFileName | string | Name of the parent process that spawned the process responsible for the event |
| InitiatingProcessParentCreationTime | datetime | Date and time when the parent of the process responsible for the event was started |
| ReportId | long | Event identifier based on a repeating counter |
| AppGuardContainerId | string | Identifier for the virtualized container used by Application Guard to isolate browser activity |
| AdditionalFields | string | Additional information about the event in JSON array format |

## Common ActionType Values

- **ProcessCreated** - A new process was created
- **ProcessTerminated** - A process was terminated

## Common Query Patterns

```kql
// Find suspicious PowerShell executions
DeviceProcessEvents
| where FileName =~ "powershell.exe"
| where ProcessCommandLine contains_any ("bypass", "hidden", "encoded")

// Hunt for living-off-the-land binaries
DeviceProcessEvents
| where FileName in~ ("certutil.exe", "regsvr32.exe", "mshta.exe", "rundll32.exe")
| where ProcessCommandLine contains_any ("http", "ftp", "download")
```
