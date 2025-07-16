# DeviceNetworkEvents

**Category:** Device Events  
**Description:** Network connection and related events from endpoints

## Schema

| Column | Type | Description |
|--------|------|-------------|
| Timestamp | datetime | Date and time when the event was recorded |
| DeviceId | string | Unique identifier for the device |
| DeviceName | string | Fully qualified domain name (FQDN) of the device |
| ActionType | string | Type of activity that triggered the event |
| RemoteIP | string | IP address that was being connected to |
| RemotePort | int | TCP port on the remote device that was being connected to |
| RemoteUrl | string | URL or fully qualified domain name (FQDN) that was being connected to |
| LocalIP | string | IP address assigned to the local device used during communication |
| LocalPort | int | TCP port on the local device used during communication |
| Protocol | string | Protocol used during the communication |
| LocalIPType | string | Type of IP address, for example Public, Private, Reserved, Loopback, Teredo, FourToSixMapping, and Broadcast |
| RemoteIPType | string | Type of IP address, for example Public, Private, Reserved, Loopback, Teredo, FourToSixMapping, and Broadcast |
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
| InitiatingProcessAccountDomain | string | Domain of the account that ran the process responsible for the event |
| InitiatingProcessAccountName | string | User name of the account that ran the process responsible for the event |
| InitiatingProcessAccountSid | string | Security Identifier (SID) of the account that ran the process responsible for the event |
| InitiatingProcessAccountUpn | string | User principal name (UPN) of the account that ran the process responsible for the event |
| InitiatingProcessAccountObjectId | string | Azure AD object ID of the user account that ran the process responsible for the event |
| InitiatingProcessLogonId | long | Identifier for a logon session of the process that initiated the event |
| InitiatingProcessIntegrityLevel | string | Integrity level of the process that initiated the event |
| InitiatingProcessTokenElevation | string | Token type indicating the presence or absence of User Access Control (UAC) privilege elevation applied to the process that initiated the event |
| ReportId | long | Event identifier based on a repeating counter |
| AppGuardContainerId | string | Identifier for the virtualized container used by Application Guard to isolate browser activity |
| AdditionalFields | string | Additional information about the event in JSON array format |

## Common ActionType Values

- **NetworkConnectionCreated** - A network connection was established
- **NetworkConnectionClosed** - A network connection was closed
- **ConnectionSuccess** - Successful network connection
- **ConnectionFailed** - Failed network connection attempt
- **InboundConnectionAccepted** - Inbound connection was accepted
- **ListeningConnectionCreated** - Process started listening on a port

## Common Query Patterns

```kql
// Find connections to suspicious domains
DeviceNetworkEvents
| where RemoteUrl has_any ("pastebin", "discord", "telegram")
| where InitiatingProcessFileName !in~ ("teams.exe", "discord.exe")

// Hunt for beaconing behavior
DeviceNetworkEvents
| where ActionType == "ConnectionSuccess"
| summarize ConnectionCount = count() by RemoteIP, InitiatingProcessFileName, bin(Timestamp, 1h)
| where ConnectionCount > 10
```
