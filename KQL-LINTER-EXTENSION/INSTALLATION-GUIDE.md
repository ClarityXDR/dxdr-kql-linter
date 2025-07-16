# KQL Schema Reference Tools - Installation Guide

## 📋 Overview
This is the **KQL Schema Reference Tools** VS Code extension that was developed during the ClarityXDR detection rules project. It provides comprehensive KQL language support, schema validation, and detection rule management for Microsoft Defender XDR and Sentinel.

## 🎯 Features
- **Multi-Platform Schema Support**: Microsoft Defender XDR and Sentinel schemas
- **Intelligent Autocompletion**: Context-aware KQL completion
- **Real-time Validation**: Instant syntax and schema validation  
- **Rich Syntax Highlighting**: Advanced KQL syntax highlighting
- **Schema Explorer**: Browse tables by category with detailed information
- **Detection Rule Templates**: Built-in templates for common detection patterns

## 📦 Installation Options

### Option 1: Install from Folder (Recommended)
1. **Copy the entire KQL-LINTER-EXTENSION folder** to your target VS Code workstation
2. **Open VS Code** on your target machine
3. **Install from folder**:
   ```bash
   # Method A: Command line installation
   code --install-extension /path/to/KQL-LINTER-EXTENSION
   
   # Method B: VS Code Extensions panel
   # 1. Open Extensions panel (Ctrl+Shift+X)
   # 2. Click "..." menu → "Install from VSIX..."
   # 3. Browse to the KQL-LINTER-EXTENSION folder
   # 4. Select the package.json file
   ```

### Option 2: Manual Development Setup
If you want to modify or develop the extension:

1. **Copy the extension folder** to your development machine
2. **Install dependencies**:
   ```powershell
   cd KQL-LINTER-EXTENSION
   npm install
   ```
3. **Open in VS Code**:
   ```powershell
   code .
   ```
4. **Run extension** (Press F5 to open Extension Development Host)

### Option 3: Package as VSIX (Alternative)
To create a portable VSIX file:

1. **Install packaging tool**:
   ```powershell
   npm install -g @vscode/vsce
   ```
2. **Navigate to extension folder**:
   ```powershell
   cd KQL-LINTER-EXTENSION
   ```
3. **Package extension**:
   ```powershell
   vsce package
   ```
4. **Install the generated .vsix file**:
   ```powershell
   code --install-extension kql-schema-reference-tools-0.1.0.vsix
   ```

## 🚀 Quick Start

### 1. Verify Installation
- Open VS Code
- Create a new file with `.kql` extension
- You should see KQL syntax highlighting automatically applied

### 2. Test Features
```kql
// Type this in a .kql file to test autocompletion
DeviceEvents
| where Timestamp > ago(1h)
| project DeviceName, ProcessCommandLine
```

### 3. Access Schema Explorer
- Open Command Palette (`Ctrl+Shift+P`)
- Type "KQL: Show Schema Explorer"
- Browse available tables and schemas

## 🔧 Configuration

### Schema Selection
The extension automatically detects context but you can manually switch:
- **Command Palette** → "KQL: Switch to XDR Schema"
- **Command Palette** → "KQL: Switch to Sentinel Schema"

### File Associations
The extension automatically activates for:
- `.kql` files
- `.kusto` files  
- `.csl` files

## 📁 Extension Contents

### Core Files
- `package.json` - Extension configuration
- `dist/extension.js` - Compiled extension code
- `language-configuration.json` - KQL language settings
- `syntaxes/kql.tmGrammar.json` - Syntax highlighting rules

### Schema Files
- `schemas/xdr/` - Microsoft Defender XDR table schemas
- `schemas/sentinel/` - Microsoft Sentinel table schemas

### Documentation
- `README.md` - Detailed extension documentation
- `CHANGELOG.md` - Version history
- `AUTO-UPDATE-FEATURE.md` - Schema update capabilities
- `DETECTION-RULE-VALIDATION.md` - Rule validation guide

## 🛠️ Troubleshooting

### Common Issues

#### Extension Not Loading
```powershell
# Check VS Code extensions
code --list-extensions | findstr kql

# Force reload VS Code
# Command Palette → "Developer: Reload Window"
```

#### Syntax Highlighting Not Working
1. Verify file extension is `.kql`, `.kusto`, or `.csl`
2. Check language mode in bottom-right of VS Code
3. Manually set language: Command Palette → "Change Language Mode" → "KQL"

#### Autocompletion Not Appearing
1. Ensure you're in a KQL file context
2. Try typing table names like `DeviceEvents`, `SecurityEvent`
3. Use `Ctrl+Space` to manually trigger completions

#### Schema Issues
1. Check if schema files exist in `schemas/` folder
2. Try switching schema context:
   - Command Palette → "KQL: Switch to XDR Schema"
   - Command Palette → "KQL: Switch to Sentinel Schema"

### Logs and Debugging
1. **Open Developer Console**: Help → Toggle Developer Tools
2. **Check Extension Host**: Look for KQL-related errors
3. **Reload Extension**: Command Palette → "Developer: Reload Window"

## 🔗 Integration with Detection Rules

This extension was specifically enhanced during the ClarityXDR project to support:
- **Detection Rule Validation**: Validate KQL queries against current schemas
- **MITRE ATT&CK Integration**: Support for technique mapping
- **SharePoint Export**: CSV export functionality for rule management
- **Template Generation**: Pre-built templates for common detection patterns

## 📊 Schema Coverage

### Microsoft Defender XDR Tables
- Device tables (DeviceEvents, DeviceProcessEvents, DeviceNetworkEvents, etc.)
- Email tables (EmailEvents, EmailAttachmentInfo, EmailUrlInfo)
- Identity tables (IdentityLogonEvents, IdentityQueryEvents)
- Alert tables (AlertInfo, AlertEvidence)

### Microsoft Sentinel Tables  
- Security tables (SecurityEvent, Syslog, AuditLogs)
- Azure tables (AzureActivity, AzureDiagnostics)
- Office 365 tables (OfficeActivity, ExchangeMailboxAudit)
- Custom tables and parsers

## 🎯 Usage Tips

### Best Practices
1. **Use schema context switching** for multi-platform queries
2. **Leverage autocompletion** for accurate table/column names
3. **Validate queries** before deploying to production
4. **Use templates** for consistent detection rule structure

### Keyboard Shortcuts
- `Ctrl+Space` - Trigger autocompletion
- `F12` - Go to definition (if available)
- `Ctrl+Shift+P` - Command palette for KQL commands

## 📈 Version Information
- **Extension Version**: 0.1.0
- **VS Code Compatibility**: ^1.101.0
- **Last Updated**: July 2025
- **Developed For**: ClarityXDR Detection Rules Project

## 🎉 Ready to Use!
The KQL linter extension is now ready for use on your VS Code workstation. Enjoy enhanced KQL development with intelligent autocompletion, validation, and schema support!

---
*This extension was developed as part of the comprehensive ClarityXDR detection rules management solution.*
