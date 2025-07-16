# KQL Schema Reference Tools

A comprehensive VS Code extension for KQL (Kusto Query Language) development with support for both Microsoft Defender XDR and Microsoft Sentinel schemas. This extension provides intelligent autocompletion, real-time validation, schema exploration, and detection rule management for security analysts and threat hunters.

## 🔥 Key Features

### Multi-Platform Schema Support
- **Microsoft Defender XDR**: Complete schema support for all XDR tables (DeviceEvents, AlertInfo, EmailEvents, etc.)
- **Microsoft Sentinel**: Full support for Sentinel/Log Analytics tables (SecurityEvent, Syslog, AuditLogs, etc.)
- **Auto-Detection**: Automatically detects query context and suggests appropriate schemas
- **Schema Switching**: Easy switching between XDR and Sentinel schema contexts

### Intelligent KQL Language Support
- **Smart Autocompletion**: Context-aware completion for tables, columns, operators, and functions
- **Real-time Validation**: Instant validation with error highlighting and suggestions
- **Performance Hints**: Built-in performance optimization suggestions
- **Syntax Highlighting**: Rich KQL syntax highlighting with table-specific coloring

### Schema Explorer
- **Interactive Tree View**: Browse tables by category and source (XDR/Sentinel)
- **Detailed Schema Information**: View complete table schemas with column details
- **Search Functionality**: Quick search across all tables and columns
- **Source Indicators**: Visual indicators for XDR vs Sentinel tables

### Detection Rule Management
- **Rule Templates**: Create detection rules with built-in templates
- **Validation**: Validate KQL queries against current schemas
- **Export/Import**: CSV export for SharePoint integration
- **MITRE ATT&CK**: Support for technique mapping and validation

## 🚀 Getting Started

### Installation
1. Install the extension from the VS Code marketplace
2. Open a `.kql` file or create a new file with KQL language mode
3. The extension will automatically activate and show the KQL schema explorer

### Quick Start
1. **Open Command Palette** (`Ctrl+Shift+P` / `Cmd+Shift+P`)
2. **Search for "KQL"** to see available commands
3. **Switch Schema Source** to choose between XDR, Sentinel, or auto-detect
4. **Start writing KQL queries** with intelligent autocompletion

## 📋 Available Commands

| Command | Description |
|---------|-------------|
| `KQL Schema Tools: Switch Schema Source` | Choose between XDR, Sentinel, or auto-detect |
| `KQL Schema Tools: Refresh Schemas` | Reload schema information |
| `KQL Schema Tools: Validate KQL Query` | Validate current KQL query |
| `KQL Schema Tools: Format KQL Query` | Format current KQL query |
| `KQL Schema Tools: Create Detection Rule` | Create new detection rule template |
| `KQL Schema Tools: Export Rules to CSV` | Export rules for SharePoint |

## ⚙️ Configuration

The extension can be configured through VS Code settings:

```json
{
  "kqlSchemaTools.defaultSchemaSource": "auto",
  "kqlSchemaTools.enableRealTimeValidation": true,
  "kqlSchemaTools.enableAutoCompletion": true,
  "kqlSchemaTools.showDeprecationWarnings": true,
  "kqlSchemaTools.mitreAttackMappingEnabled": true
}
```

### Configuration Options

- **`defaultSchemaSource`**: Default schema source (`"auto"`, `"xdr"`, `"sentinel"`)
- **`enableRealTimeValidation`**: Enable real-time validation as you type
- **`enableAutoCompletion`**: Enable auto-completion features
- **`showDeprecationWarnings`**: Show warnings for deprecated tables/columns
- **`mitreAttackMappingEnabled`**: Enable MITRE ATT&CK technique mapping

## 🛡️ Schema Sources

### Microsoft Defender XDR Tables
- **Device Tables**: DeviceEvents, DeviceFileEvents, DeviceNetworkEvents, etc.
- **Email Tables**: EmailEvents, EmailPostDeliveryEvents, EmailUrlInfo, etc.
- **Identity Tables**: IdentityLogonEvents, IdentityQueryEvents, etc.
- **Alert Tables**: AlertInfo, AlertEvidence
- **Cloud Tables**: CloudAppEvents, BehaviorAnalytics

### Microsoft Sentinel Tables
- **Security Tables**: SecurityEvent, SecurityAlert, SecurityIncident
- **System Tables**: Syslog, Event, Heartbeat, Perf
- **Azure Tables**: AzureActivity, AuditLogs, SigninLogs
- **Office 365**: OfficeActivity, various AAD tables
- **Cloud Providers**: AWSCloudTrail, GCPAuditLogs

## 💡 Usage Examples

### Basic Query with Autocompletion
```kql
DeviceEvents
| where Timestamp > ago(1d)
| where ActionType == "ProcessCreated"
| project Timestamp, DeviceName, ProcessCommandLine
```

### Cross-Platform Query Detection
The extension automatically detects whether you're writing XDR or Sentinel queries:
```kql
// XDR Query - uses Timestamp
DeviceEvents | where Timestamp > ago(1h)

// Sentinel Query - uses TimeGenerated  
SecurityEvent | where TimeGenerated > ago(1h)
```

### Performance Optimization Hints
The extension provides performance suggestions:
- Add time filters for better performance
- Avoid leading wildcards in string searches
- Use appropriate limits for large result sets

## 🔧 Advanced Features

### Schema Validation
- **Table Existence**: Validates that referenced tables exist in the current schema
- **Column Validation**: Checks column names against table schemas
- **Type Checking**: Validates data types and operations
- **Deprecation Warnings**: Alerts about deprecated tables or columns

### Performance Analysis
- **Query Optimization**: Suggests performance improvements
- **Resource Usage**: Warns about potentially expensive operations
- **Best Practices**: Recommends KQL best practices

### Detection Rule Features
- **Template Generation**: Creates rule templates with metadata
- **MITRE Mapping**: Supports MITRE ATT&CK technique attribution
- **CSV Export**: SharePoint-ready CSV export format
- **Validation**: Comprehensive rule validation

## 📁 File Structure

For custom schema files, organize them in your workspace:
```
workspace/
├── schemas/
│   ├── xdr/
│   │   ├── DeviceEvents.md
│   │   └── AlertInfo.md
│   └── sentinel/
│       ├── SecurityEvent.md
│       └── Syslog.md
└── queries/
    ├── threat-hunting.kql
    └── detection-rules.kql
```

## 🤝 Contributing

This extension is designed to be portable and easily extensible. Contributions are welcome for:
- Additional schema sources
- Enhanced validation rules
- New detection rule templates
- Performance optimization suggestions

## 📊 Supported Platforms

- **Microsoft Defender XDR** (formerly Microsoft 365 Defender)
- **Microsoft Sentinel** (formerly Azure Sentinel)
- **Azure Data Explorer** (Kusto)
- **Azure Monitor Logs**

## 🔍 Troubleshooting

### Common Issues
1. **Schemas not loading**: Check workspace folder structure and permissions
2. **Autocompletion not working**: Ensure file language is set to "KQL"
3. **Validation errors**: Verify schema source matches your query context

### Status Bar Indicator
The status bar shows the current schema source (e.g., "KQL: XDR" or "KQL: SENTINEL"). Click to change the source.

## 📝 Changelog

### Version 0.1.0
- Initial release with XDR and Sentinel schema support
- Real-time validation and autocompletion
- Schema explorer and detection rule management
- Performance optimization hints
- CSV export functionality

---

**Enjoy enhanced KQL development with comprehensive schema support!** 🎯

## Following extension guidelines

Ensure that you've read through the extensions guidelines and follow the best practices for creating your extension.

* [Extension Guidelines](https://code.visualstudio.com/api/references/extension-guidelines)

## Working with Markdown

You can author your README using Visual Studio Code. Here are some useful editor keyboard shortcuts:

* Split the editor (`Cmd+\` on macOS or `Ctrl+\` on Windows and Linux).
* Toggle preview (`Shift+Cmd+V` on macOS or `Shift+Ctrl+V` on Windows and Linux).
* Press `Ctrl+Space` (Windows, Linux, macOS) to see a list of Markdown snippets.

## For more information

* [Visual Studio Code's Markdown Support](http://code.visualstudio.com/docs/languages/markdown)
* [Markdown Syntax Reference](https://help.github.com/articles/markdown-basics/)

**Enjoy!**
