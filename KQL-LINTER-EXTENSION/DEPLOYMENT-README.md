# KQL Schema Reference Tools - Deployment Package

## Overview
This deployment package contains the essential files for the **KQL Schema Reference Tools** VS Code extension for Microsoft Defender XDR and Sentinel.

## Package Contents

### Core Extension Files
- `package.json` - Extension manifest and configuration
- `dist/extension.js` - Compiled extension code
- `language-configuration.json` - KQL language configuration
- `syntaxes/kql.tmGrammar.json` - KQL syntax highlighting grammar

### Schema Files
- `schemas/xdr/` - Microsoft Defender XDR table schemas
- `schemas/sentinel/` - Microsoft Sentinel table schemas

### Documentation
- `README.md` - Main extension documentation
- `CHANGELOG.md` - Version history and changes
- `AUTO-UPDATE-FEATURE.md` - Schema auto-update feature documentation
- `DETECTION-RULE-VALIDATION.md` - Detection rule validation guide

## Installation Options

### Option 1: Install from VSIX (Recommended)
If you have the pre-built VSIX file:
```bash
code --install-extension kql-schema-reference-tools-0.1.0.vsix
```

### Option 2: Build and Install from Source
1. Copy this deployment package to your development machine
2. Open terminal in the package directory
3. Install dependencies: `npm install`
4. Build the extension: `npm run build`
5. Package the extension: `npx vsce package`
6. Install: `code --install-extension kql-schema-reference-tools-0.1.0.vsix`

### Option 3: Development Mode
1. Copy the deployment package to your VS Code extensions directory:
   - Windows: `%USERPROFILE%\.vscode\extensions\`
   - macOS: `~/.vscode/extensions/`
   - Linux: `~/.vscode/extensions/`
2. Restart VS Code

## Key Features
- **Schema Validation**: Real-time KQL query validation against XDR and Sentinel schemas
- **Auto-Update**: Automatically fetch latest schemas from Microsoft Learn
- **Detection Rules**: Create and validate Defender XDR Custom Detection Rules
- **Syntax Highlighting**: Full KQL syntax highlighting and IntelliSense
- **MITRE ATT&CK**: Technique mapping and validation

## Quick Start
1. Install the extension using one of the methods above
2. Open a `.kql` file or create a new one
3. Use commands via Ctrl+Shift+P:
   - "KQL: Update Schemas" - Fetch latest schemas
   - "KQL: Validate Detection Rule" - Validate custom detection rules
   - "KQL: Show Schema Tree" - Browse available tables and columns

## Requirements
- VS Code 1.60.0 or higher
- Internet connection for schema auto-updates

## Support
For issues and feature requests, please refer to the main repository or documentation files included in this package.
