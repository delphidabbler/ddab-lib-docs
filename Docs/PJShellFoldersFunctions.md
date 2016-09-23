# Shell Folders Public Routines #

**Project:** [Shell Folders Unit](ShellFoldersUnit.md).

**Unit:** _PJShellFolders_.

The following public routines are defined in _PJShellFolders_:

  * [IsValidSpecialFolderId](#isvalidspecialfolderid)
  * [NumSpecialFolderIds](#numspecialfolderids)
  * [SpecialFolderIdToStr](#specialfolderidtostr)
  * [StrToSpecialFolderID](#strtospecialfolderid)
  * [PIDLToFolderPath](#pidltofolderpath)
  * [PIDLToFolderDisplayName](#pidltofolderdisplayname)

## IsValidSpecialFolderId ##

```pascal
function IsValidSpecialFolderId(ID: Integer): Boolean;
```

Returns true if the given special folder identifier is defined by Windows and supported by this unit.

This test can be performed to check an identifier value before passing to _[SpecialFolderIdToStr](#specialfolderidtostr)_ or before setting the _[TPJSpecialFolderInfo](TPJSpecialFolderInfo.md)_ component's _[FolderID](TPJSpecialFolderInfoFolderID.md)_ property to avoid exception being raised by an invalid value.

### Tip ###

Use the _[TPJSpecialFolderEnum](TPJSpecialFolderEnum.md)_ class to enumerate all the valid folder identifiers.

## NumSpecialFolderIds ##

```pascal
function NumSpecialFolderIds: Integer;
```

Returns the number of special folder identifiers defined by Windows that are supported by this unit.

## SpecialFolderIdToStr ##

```pascal
function SpecialFolderIdToStr(ID: Integer): string;
```

Returns the string representation of the constant identifier used by Windows to identify a special folder.

Windows defines identifiers to represent the shell's special folders. The _ShlObj_ unit defines symbolic constants for these values. Passing an indentifier value to this function causes the name of the associated symbolic constant to be returned as a string. If the value is not a valid special folder indentifier the an exception is raised.

### Tips ###

To check if an identifier value is valid use the _[IsValidSpecialFolderId](#isvalidspecialfolderid)_ function.

Use the _[TPJSpecialFolderEnum](TPJSpecialFolderEnum.md)_ class to enumerate all the valid folder identifiers.

### Example ###

`SpecialFolderIdToStr(4)` returns `'CSIDL_PRINTERS'`.

## StrToSpecialFolderID ##

```pascal
function StrToSpecialFolderID(const IDStr: string): Integer;
```

Returns the value of the special folder identifier associated with the Windows symbolic constant.

Windows defines identifiers to represent the shell's special folders. The _ShlObj_ unit defines symbolic constants for these values. Passing the string representation of one of these constants to this function returns the constant's value.  Passing an invalid constant name causes an exception to be raised.

### Example ###

`StrToSpecialFolderId('CSIDL_PRINTERS')` returns `4`.

## PIDLToFolderPath ##

```pascal
function PIDLToFolderPath(PIDL: PItemIDList): string;
```

Returns the path of the folder described by PIDL.

## PIDLToFolderDisplayName ##

```pascal
function PIDLToFolderDisplayName(PIDL: PItemIDList): string;
```

Returns the display name of the folder described by PIDL.
