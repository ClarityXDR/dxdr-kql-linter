# DeviceFileEvents

**Category:** Device Events  
**Description:** File creation, modification, and other filesystem events

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
| FileOriginUrl | string | URL where the file was downloaded from |
| FileOriginReferrerUrl | string | URL of the web page that referred to the downloaded file |
| FileOriginIP | string | IP address where the file was downloaded from |
| PreviousFileName | string | Original name of the file before the action that resulted in the recorded event |
| PreviousFolderPath | string | Original folder containing the file before the action that resulted in the recorded event |
| FileSize | long | Size of the file in bytes |
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
| RequestAccountDomain | string | Domain of the account used to remotely initiate the activity |
| RequestAccountName | string | User name of account used to remotely initiate the activity |
| RequestAccountSid | string | Security Identifier (SID) of the account used to remotely initiate the activity |
| RequestSourceIP | string | IPv4 or IPv6 address of the remote device that initiated the activity |
| RequestSourcePort | int | Source port on the remote device that initiated the activity |
| RequestProtocol | string | Network protocol, if applicable, used to initiate the activity (Unknown, Local, SMB, or NFS) |
| ShareName | string | Name of shared folder containing the file |
| IsAzureInfoProtectionApplied | bool | Indicates whether the file is encrypted by Azure Information Protection |
| ReportId | long | Event identifier based on a repeating counter |
| AppGuardContainerId | string | Identifier for the virtualized container used by Application Guard to isolate browser activity |
| AdditionalFields | string | Additional information about the event in JSON array format |
| SensitivityLabel | string | Label applied to an email, file, or other content to classify it for information protection |
| SensitivitySubLabel | string | Sublabel applied to an email, file, or other content to classify it for information protection |

## Common ActionType Values

- **FileCreated** - File was created
- **FileModified** - File was modified
- **FileDeleted** - File was deleted
- **FileRenamed** - File was renamed
- **FileCopied** - File was copied
- **FileMoved** - File was moved

## Common Query Patterns

```kql
// Hunt for suspicious file downloads
DeviceFileEvents
| where ActionType == "FileCreated"
| where FileOriginUrl != ""
| where FileName endswith_any (".exe", ".scr", ".bat", ".ps1")

// Monitor sensitive file access
DeviceFileEvents
| where FolderPath contains_any ("confidential", "secret", "password")
| where ActionType in ("FileModified", "FileCopied", "FileDeleted")
```
