# VersionInfo property

**Project:** [About Box Component](../API.md)

**Unit:** _PJAbout_.

**Class:** [_TPJAboutBoxDlg_](./TPJAboutBoxDlg.md)

```pascal
property VersionInfo: TPJVersionInfo;
```

## Description

This property allows information from a string information block in a program file's _VERSIONINFO_ resource to be displayed in the dialog box.

To enable this to happen a [_TPJVersionInfo_](../../VerInfo/API/TPJVersionInfo.md) component must be placed on the form and this property must reference it. The _TPJVersionInfo_ component's [_FileName_](../../VerInfo/API/TPJVersionInfo-FileName.md) property must be set to the name of the executable file from which version information is to be extracted, or set to '' to get the version information of the parent executable file.

The following table shows which version information string values are used, along with the properties whose values they replace:

| _VERSIONINFO_ string  | Replaces property |
|-----------------------|-------------------|
| ProductName | [_ProgramName_](./TPJAboutBoxDlg-ProgramName.md) |
| ProductVersion | [_Version_](./TPJAboutBoxDlg-Version.md) |
| LegalCopyright | [_Copyright_](./TPJAboutBoxDlg-Copyright.md) |
| Comments | [_Notes_](./TPJAboutBoxDlg-Notes.md) |

If any of these string values are not present in the version information nothing is displayed in their place.

If the _VersionInfo_ property is set to nil then the information displayed in the dialog box is taken from the string properties listed in the table above.

This property has no effect on the [_Title_](./TPJAboutBoxDlg-Title.md) property.
