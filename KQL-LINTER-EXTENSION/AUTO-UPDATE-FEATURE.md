# KQL Schema Auto-Update Feature

## 🔄 Automatic Schema Updates from Microsoft Learn

Your KQL Schema Reference Tools extension now automatically fetches the latest Defender XDR table schemas directly from Microsoft Learn documentation!

## ✨ Features

### **Real-time Schema Updates**
- ✅ Automatically pulls latest table schemas from [Microsoft Learn](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- ✅ Includes new tables like `ExposureGraphNodes`, `ExposureGraphEdges`, etc.
- ✅ Updates column definitions and descriptions
- ✅ Maintains local cache for offline use

### **Smart Update Management**
- ✅ **Auto-check on startup** (configurable)
- ✅ **Manual update command** via Command Palette
- ✅ **Configurable update intervals** (default: 24 hours)
- ✅ **Progress notifications** during updates

## 🚀 How to Use

### **Manual Update**
1. Press `Ctrl+Shift+P`
2. Search for "KQL: Update Schemas from Microsoft Learn"
3. Wait for the update to complete

### **Check Schema Explorer**
- Open the **KQL Tools** panel in the sidebar
- Browse the latest XDR table schemas
- Click any table to see detailed column information

### **Configure Auto-Updates**
Go to VS Code Settings (`Ctrl+,`) and search for "KQL":

```json
{
  "kqlSchemaTools.autoUpdateSchemas": true,        // Enable auto-updates
  "kqlSchemaTools.updateCheckInterval": 24        // Hours between checks
}
```

## 📊 What Gets Updated

The extension automatically fetches:

- **All current XDR tables** including latest additions
- **Column names and data types** 
- **Table descriptions and categories**
- **Documentation links** to Microsoft Learn
- **Common use cases and sample queries**

## 🎯 Benefits for You

1. **Always Current** - Never use outdated table/column names
2. **Zero Maintenance** - No manual schema file updates needed  
3. **New Table Discovery** - Automatically learn about new XDR tables
4. **Accurate Validation** - Real-time validation against current schemas
5. **Better Queries** - IntelliSense with latest column names

## 🔧 Technical Details

- **Source**: [Microsoft Learn Defender XDR Documentation](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- **Update Method**: HTTPS scraping of official documentation
- **Storage**: Local markdown files in extension directory
- **Backup**: Original static schemas available as fallback
- **Performance**: Minimal impact, updates in background

## 🚨 Never Write Wrong KQL Again!

With auto-updating schemas, you'll always have:
- ✅ Current table names
- ✅ Accurate column names  
- ✅ Latest data types
- ✅ New XDR capabilities

**The extension now keeps itself updated with Microsoft's latest XDR schema changes automatically!** 🎉
