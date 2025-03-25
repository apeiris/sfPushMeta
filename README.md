
# Adding Picklist Value to Status__c Field in Order__c Object

This guide explains how to add a new picklist value to the Status__c field in the Order__c custom object using Salesforce Metadata API through VS Code.

## Prerequisites

- VS Code with Salesforce Extension Pack installed
- Salesforce CLI installed and configured
- Connected to a Salesforce org
- Existing project with source retrieval

## Steps

1. **Retrieve Existing Metadata**
   - Open VS Code
   - Open the Command Palette (Ctrl+Shift+P / Cmd+Shift+P)
   - Run: `SFDX: Retrieve Source from Org`
   - In the package.xml, ensure you have:

   ```xml
     <types>
         <members>Order__c</members>
         <name>CustomObject</name>
     </types>
2. **Modify Custom Object Metadata**

    - Navigate to force-app/main/default/objects/Order__c/
    - Open Order__c.object-meta.xml
    - Find the `<fields>` section for Status__c
    It should look similar to:

```xml
    <fields>
        <fullName>Status__c</fullName>
        <type>Picklist</type>
        <valueSet>
            <valueSetDefinition>
                <sorted>false</sorted>
                <value>
                    <fullName>ExistingValue1</fullName>
                    <default>false</default>
                    <label>Existing Value 1</label>
                </value>
                <!-- Other existing values -->
            </valueSetDefinition>
        </valueSet>
    </fields>
```

3. **Add new Picklist value**

 Within the `<valueSetDefinition>` tags, add your new value:

```xml
<value>
    <fullName>NewItem</fullName>
    <default>false</default>
    <label>New Item</label>
</value>```
Example with new value added:

```xml

<fields>
    <fullName>Status__c</fullName>
    <type>Picklist</type>
    <valueSet>
        <valueSetDefinition>
            <sorted>false</sorted>
            <value>
                <fullName>ExistingValue1</fullName>
                <default>false</default>
                <label>Existing Value 1</label>
            </value>
            <value>
                <fullName>NewItem</fullName>
                <default>false</default>
                <label>New Item</label>
            </value>
        </valueSetDefinition>
    </valueSet>
</fields>
```

## Deploy Changes

 -   Save the modified file
 -   Right-click the file in VS Code
        Select SFDX: Deploy Source to Org
    Or
 -    use terminal:
     sfdx force:source:deploy -p force-app/main/default/objects/Order__c

## Folder Structure
```plaintext
force-app/
├── main/
│   ├── default/
│   │   ├── objects/
│   │   │   ├── Order__c/
│   │   │   │   ├── Order__c.object-meta.xml
│   │   │   │   ├── fields/
│   │   │   │   └── ...
└── README.md
```




"# sfPushMeta" 
