<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# VersionInfo property #

**Project:** [About Box Component](AboutBoxComponent.md).

**Unit:** _PJAbout_.

**Class:** _[TPJAboutBoxDlg](TPJAboutBoxDlg.md)_

```
property VersionInfo: TPJVersionInfo;
```

## Description ##

This property allows information from a string information block in a program file's _VERSIONINFO_ resource to be displayed in the dialog box.

To enable this to happen a _[TPJVersionInfo](TPJVersionInfo.md)_ component must be placed on the form and this property must reference it. The _TPJVersionInfo_ component's _[FileName](TPJVersionInfoFileName.md)_ property must be set to the name of the executable file from which version information is to be extracted, or set to '' to get the version information of the parent executable file.

The following table shows which version information string values are used, along with the properties whose values they replace:

| **VERSIONINFO string** | Replaces property |
|:-----------------------|:------------------|
| ProductName | _[ProgramName](TPJAboutBoxDlgProgramName.md)_ |
| ProductVersion | _[Version](TPJAboutBoxDlgVersion.md)_ |
| LegalCopyright | _[Copyright](TPJAboutBoxDlgCopyright.md)_ |
| Comments | _[Notes](TPJAboutBoxDlgNotes.md)_ |

If any of these string values are not present in the version information nothing is displayed in their place.

If the _VersionInfo_ property is set to nil then the information displayed in the dialog box is taken from the string properties listed in the table above.

This property has no effect on the _[Title](TPJAboutBoxDlgTitle.md)_ property.