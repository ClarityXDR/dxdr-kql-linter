# SecurityEvent

The SecurityEvent table contains Windows security events from devices being monitored by Microsoft Sentinel.

This table provides detailed information about authentication, authorization, and other security-related activities on Windows systems.

## Columns

| Column name | Data type | Description |
|-------------|-----------|-------------|
| TimeGenerated | datetime | The time at which the event was generated |
| Computer | string | The computer on which the event occurred |
| EventID | int | The event identifier |
| EventData | string | Event-specific data |
| EventSourceName | string | The source that generated the event |
| Activity | string | The activity or operation that was audited |
| SubjectUserSid | string | The SID of the subject (user) |
| SubjectUserName | string | The account name of the subject |
| SubjectDomainName | string | The domain name of the subject |
| SubjectLogonId | string | The logon ID of the subject |
| TargetUserSid | string | The SID of the target user |
| TargetUserName | string | The account name of the target user |
| TargetDomainName | string | The domain name of the target user |
| LogonType | int | The type of logon that was performed |
| LogonProcessName | string | The name of the logon process |
| AuthenticationPackageName | string | The name of the authentication package |
| WorkstationName | string | The name of the workstation |
| LogonGuid | string | The GUID that identifies the logon session |
| TransmittedServices | string | Services that were transmitted to the destination computer |
| LmPackageName | string | The name of the LAN Manager sub-package |
| KeyLength | int | The length of the session key |
| ProcessId | string | The ID of the process |
| ProcessName | string | The name of the process |
| IpAddress | string | The IP address of the machine from which a logon attempt was made |
| IpPort | string | The source port on the client machine |
| ImpersonationLevel | string | The impersonation level |
| RestrictedAdminMode | string | Indicates if Restricted Admin mode was used |
| TargetOutboundUserName | string | The name of the target outbound user |
| TargetOutboundDomainName | string | The domain of the target outbound user |
| VirtualAccount | string | Indicates if the account is a virtual account |
| TargetLinkedLogonId | string | The linked logon session identifier |
| ElevatedToken | string | Indicates if the token is elevated |

[Official Documentation](https://docs.microsoft.com/en-us/azure/sentinel/normalization-schema-authentication)
