# DeviceEvents

The DeviceEvents table contains information about various events on devices, including process execution, file operations, and system events.

This table is part of the Microsoft Defender XDR schema and provides comprehensive device telemetry for threat hunting and investigation.

## Columns

| Column name | Data type | Description |
|-------------|-----------|-------------|
| Timestamp | datetime | Date and time when the event was recorded |
| DeviceId | string | Unique identifier for the device |
| DeviceName | string | Fully qualified domain name (FQDN) of the device |
| ActionType | string | Type of activity that triggered the event |
| FileName | string | Name of the file that the recorded action was applied to |
| FolderPath | string | Folder containing the file that the recorded action was applied to |
| SHA1 | string | SHA-1 hash of the file that the recorded action was applied to |
| SHA256 | string | SHA-256 hash of the file that the recorded action was applied to |
| MD5 | string | MD5 hash of the file that the recorded action was applied to |
| ProcessId | int | Process ID (PID) of the newly created process |
| ProcessCommandLine | string | Command line used to create the new process |
| ProcessCreationTime | datetime | Date and time the process was created |
| AccountDomain | string | Domain of the account |
| AccountName | string | User name of the account |
| AccountSid | string | Security Identifier (SID) of the account |
| LogonId | string | Identifier for a logon session |
| InitiatingProcessId | int | Process ID (PID) of the parent process |
| InitiatingProcessCreationTime | datetime | Date and time when the parent process was started |
| InitiatingProcessFileName | string | Name of the process that initiated the event |
| InitiatingProcessCommandLine | string | Command line used to run the process that initiated the event |
| ReportId | long | Event identifier based on a repeating counter |
| AppGuardContainerId | string | Identifier for the virtualized container used by Application Guard to isolate browser activity |
| AdditionalFields | dynamic | Additional information about the event in JSON array format |

[Official Documentation](https://docs.microsoft.com/en-us/microsoft-365/security/defender/advanced-hunting-deviceevents-table)
