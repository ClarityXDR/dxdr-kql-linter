# 🛡️ Custom Detection Rule Validation

## **Zero-Error Detection Rules for Defender XDR**

Your KQL Schema Reference Tools extension now includes **comprehensive Custom Detection Rule validation** to ensure your queries meet all Defender XDR requirements before deployment!

## 🎯 **What Gets Validated**

### **✅ Required Columns**
1. **Timestamp** - Must be present and unmanipulated
2. **Unique Identifiers** - Based on table type:
   - **Device tables**: `DeviceId` + `ReportId` + `Timestamp`
   - **Alert tables**: `Timestamp` only
   - **Observation tables**: `ObservationId` + `Timestamp`
   - **Other tables**: `ReportId` + `Timestamp`
3. **Impacted Asset** - At least one of:
   - `DeviceId`, `DeviceName`, `RemoteDeviceName`
   - `RecipientEmailAddress`, `SenderFromAddress`, `SenderMailFromAddress`
   - `AccountObjectId`, `AccountSid`, `AccountUpn`
   - And 10+ other asset identifiers

### **⚡ Continuous (NRT) Compatibility**
- **Single table only** - No joins or unions
- **Supported tables** - 20+ tables including all Device*, Email*, Alert*, Identity* tables
- **No comments** - Comments break NRT processing
- **Supported operators** - Validates against NRT operator restrictions

### **🚨 Common Issues Detected**
- ❌ Missing `Timestamp` column
- ❌ Missing unique identifiers for alert correlation
- ❌ Missing impacted asset columns
- ❌ NRT-incompatible operators (join, union, externaldata)
- ❌ Multiple table references (breaks NRT)
- ❌ Comments in query (breaks NRT)

## 🚀 **How to Use**

### **Manual Validation**
1. Open any `.kql` file
2. Press `Ctrl+Shift+P`
3. Search: **"KQL: Validate Custom Detection Rule"**
4. View detailed validation results

### **Generate Templates**
1. Press `Ctrl+Shift+P`
2. Search: **"KQL: Generate Detection Rule Template"**
3. Select a table (DeviceProcessEvents, EmailEvents, etc.)
4. Get a pre-built template with all required columns

### **Right-Click Context Menu**
- Right-click in any KQL file
- Select **"Validate Custom Detection Rule"**
- Get instant feedback

## 📊 **Validation Results Explained**

The validator provides comprehensive feedback:

```
🛡️  CUSTOM DETECTION RULE VALIDATION RESULTS
==================================================
✅ Detection rule is VALID and ready for deployment!

📋 REQUIRED COLUMNS STATUS:
├─ Timestamp column: ✅
├─ Unique identifiers: ✅
└─ Impacted asset: ✅

✅ Found required columns:
   • Timestamp
   • DeviceId
   • ReportId
   • DeviceName

⚡ CONTINUOUS (NRT) COMPATIBILITY:
✅ Query supports Continuous (NRT) frequency for near real-time detection

💡 RECOMMENDATIONS:
   • ✅ Query is compatible with Continuous (NRT) frequency for faster threat detection
```

## 🔧 **Detection Rule Requirements Reference**

### **Required Columns by Table Type**

| Table Type | Required Columns |
|------------|------------------|
| **Device*** | `Timestamp`, `DeviceId`, `ReportId` |
| **Alert*** | `Timestamp` only |
| **Observation*** | `Timestamp`, `ObservationId` |
| **Email***, **Identity***, others | `Timestamp`, `ReportId` |

### **Impacted Asset Columns**
- `DeviceId`, `DeviceName`, `RemoteDeviceName`
- `RecipientEmailAddress`, `SenderFromAddress`, `SenderMailFromAddress`
- `RecipientObjectId`, `AccountObjectId`, `AccountSid`, `AccountUpn`
- `InitiatingProcessAccountSid`, `InitiatingProcessAccountUpn`, `InitiatingProcessAccountObjectId`

### **NRT-Compatible Tables**
- All **Device*** tables (DeviceProcessEvents, DeviceNetworkEvents, etc.)
- All **Email*** tables (EmailEvents, EmailAttachmentInfo, etc.)
- All **Identity*** tables (IdentityLogonEvents, etc.)
- **AlertEvidence**, **CloudAppEvents**, **UrlClickEvents**

## 🎯 **Sample Templates**

### **Device Process Detection**
```kql
DeviceProcessEvents
| where Timestamp > ago(1d)
| where ActionType == "ProcessCreated"
| where FileName =~ "powershell.exe"
| where ProcessCommandLine contains "bypass"
| project 
    Timestamp,                    // Required
    DeviceId,                     // Required
    ReportId,                     // Required
    DeviceName,                   // Impacted asset
    AccountName,                  // Context
    ProcessCommandLine            // Evidence
```

### **Email Threat Detection**
```kql
EmailEvents
| where Timestamp > ago(1d)
| where ThreatTypes has "Phish"
| where DeliveryAction == "Delivered"
| project 
    Timestamp,                    // Required
    ReportId,                     // Required
    RecipientEmailAddress,        // Impacted asset
    SenderFromAddress,            // Context
    Subject,                      // Evidence
    AttachmentCount               // Evidence
```

## 🚨 **Zero Tolerance for Detection Rule Errors**

With this validator:
- ✅ **Never deploy broken detection rules**
- ✅ **Always meet Defender XDR requirements**
- ✅ **Optimize for Continuous (NRT) when possible**
- ✅ **Get clear guidance on fixing issues**

**Your detection rules will work perfectly in Defender XDR every time!** 🎉
