<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# ProgramName property #

**Project:** [About Box Component](AboutBoxComponent.md).

**Unit:** _PJAbout_.

**Class:** _[TPJAboutBoxDlg](TPJAboutBoxDlg.md)_

```
property ProgramName: string;
```

## Description ##

The _ProgramName_ property defines the program name to be displayed on the first line of the about box.

If _ProgramName_ is set to the empty string then the title of the application as specified by the _Title_ property of the _Application_ object is displayed. If you have not specified an application title then the name of the project (without the `.dpr` extension) is used. If _ProgramName_ is set to any non-empty string then that string is displayed.

_ProgramName_ defaults to the empty string.

Note: If the _[VersionInfo](TPJAboutBoxDlgVersionInfo.md)_ property is not nil then _ProgramName_ is ignored.