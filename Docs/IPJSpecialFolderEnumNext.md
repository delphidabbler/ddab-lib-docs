# Next method #

**Project:** [Shell Folders Unit](ShellFoldersUnit.md).

**Unit:** _PJShellFolders_.

**Interface:** _[IPJSpecialFolderEnum](IPJSpecialFolderEnum.md)_

```pascal
function Next: Integer;
```

## Description ##

The _Next_ method returns the value of the next special folder in the enumeration. If _Next_ is called when the enumeration is at an end then -1 is returned. To reinitialise the enumeration call _[Init](IPJSpecialFolderEnumInit.md)_.