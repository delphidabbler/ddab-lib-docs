# TPJSpecialFolderEnum #

**Project:** [Shell Folders Unit](ShellFoldersUnit.md).

**Unit:** _PJShellFolders_.

Windows defines integer identifiers to represent the shell's special folders. _TPJSpecialFolderEnum_ is a class that enumerates the values of all the special folder identifiers.

The key method is the _[Next](TPJSpecialFolderEnumNext.md)_ method which returns a sequence of identifiers each time it called. The _[Init](TPJSpecialFolderEnumInit.md)_ methods re-intialises the enumeration and the _[AtEnd](TPJSpecialFolderEnumAtEnd.md)_ methods returns true when all the identifiers have been returned. The number of identifiers in the enumeration are given by the _[Count](TPJSpecialFolderEnumCount.md)_ method.

_TPJSpecialFolderEnum_ implements the _[IPJSpecialFolderEnum](IPJSpecialFolderEnum.md)_ interface.

An [example](PJShellFoldersExample.md) of using _TPJSpecialFolderEnum_ is provided.

## Methods ##

| **Method** | **Description** |
|:-----------|:----------------|
| _[AtEnd](TPJSpecialFolderEnumAtEnd.md)_ | Tests whether the end of the enumeration has been reached. |
| _[Count](TPJSpecialFolderEnumCount.md)_ | Returns the number of special folder identifiers in the enumeration. |
| _[Create](TPJSpecialFolderEnumCreate.md)_ | Constructs and intialises a _TPJSpecialFolderEnum_ object. |
| _[Init](TPJSpecialFolderEnumInit.md)_ | Reinitialises the enumeration. |
| _[Next](TPJSpecialFolderEnumNext.md)_ | Returns the next identifier in the enumeration. |

## Properties ##

_TPJSpecialFolderEnum_ defines no properties.

## Events ##

_TPJSpecialFolderEnum_ defines no events.