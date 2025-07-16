# Defender XDR Table Reference

This directory contains comprehensive schema documentation for Microsoft Defender XDR tables.

## Device Tables

- **[DeviceEvents](DeviceEvents.md)** - Miscellaneous device events
- **[DeviceProcessEvents](DeviceProcessEvents.md)** - Process creation and termination
- **[DeviceNetworkEvents](DeviceNetworkEvents.md)** - Network connections and communications
- **[DeviceFileEvents](DeviceFileEvents.md)** - File operations and modifications
- **DeviceRegistryEvents** - Registry key and value modifications
- **DeviceLogonEvents** - Sign-ins and authentication events
- **DeviceImageLoadEvents** - DLL loading events
- **DeviceInfo** - Device information and configuration

## Email & Collaboration Tables

- **[EmailEvents](EmailEvents.md)** - Email delivery, blocking, and post-delivery events
- **EmailPostDeliveryEvents** - Actions taken on emails after delivery
- **EmailAttachmentInfo** - Information about email attachments
- **EmailUrlInfo** - Information about URLs in emails

## Identity Tables

- **IdentityLogonEvents** - Authentication activities involving on-premises Active Directory
- **IdentityQueryEvents** - Queries for Active Directory objects
- **IdentityDirectoryEvents** - Events involving an on-premises domain controller

## Cloud App Tables

- **CloudAppEvents** - Events from various cloud apps and services

## Alert Tables

- **AlertEvidence** - Files, IP addresses, URLs, users, or devices associated with alerts
- **AlertInfo** - Alerts from Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Microsoft Defender for Cloud Apps, and Microsoft Defender for Identity

## Threat Intelligence Tables

- **ThreatIntelligenceIndicators** - Threat intelligence indicators from various sources

## Advanced Hunting Functions

### Time Functions
- `ago()` - Returns a time relative to now
- `now()` - Returns current UTC time
- `datetime()` - Creates datetime values
- `bin()` - Rounds values down to datetime bins

### String Functions
- `contains` - Case-insensitive substring search
- `contains_cs` - Case-sensitive substring search
- `has` - Searches for whole words
- `has_any` - Searches for any of the specified strings
- `startswith` - String starts with specified value
- `endswith` - String ends with specified value
- `matches regex` - Regular expression matching

### Aggregation Functions
- `count()` - Count of rows
- `dcount()` - Distinct count
- `sum()` - Sum of values
- `avg()` - Average of values
- `min()` - Minimum value
- `max()` - Maximum value

### Common Operators
- `where` - Filter rows
- `project` - Select specific columns
- `extend` - Add calculated columns
- `summarize` - Group and aggregate data
- `join` - Combine data from multiple tables
- `union` - Combine rows from multiple tables
- `limit` - Restrict number of results
- `sort by` - Order results
