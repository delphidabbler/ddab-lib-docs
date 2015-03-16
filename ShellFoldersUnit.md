<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# Shell Folders Unit #

Two units are actually provided: _PJShellFolders_ and _PJShellFoldersDsgn_.

## PJShellFolders ##

This unit provides components, classes and routines to assist in working with shell folders. There are two components:

  * _[TPJSpecialFolderInfo](TPJSpecialFolderInfo.md)_ - provides information about the Shell's various special folders.
  * _[TPJBrowseDialog](TPJBrowseDialog.md)_ - provides access to the Browse for Folder dialog box.

There is also a class - _[TPJSpecialFolderEnum](TPJSpecialFolderEnum.md)_ that enumerates the shell's special folder identifiers. This class implements the _[IPJSpecialFolderEnum](IPJSpecialFolderEnum.md)_ interface. Functions that provide information about the special folder identifiers and symbolic constants are also provided.

_PJShellFolders_ also provides [functions](PJShellFoldersFunctions.md) to provide information about the folders described by PIDLs.

## PJShellFoldersDsgn ##

This unit provides design time support. In particular it provides a property editor for _[TPJBrowseDialog](TPJBrowseDialog.md)_ and _[TPJSpecialFolderInfo](TPJSpecialFolderInfo.md)_ that allows predefined special folder IDs to be selected in the object inspector.

**Links:**

  * Back to [Wiki Home Page](Welcome.md)
  * [Shell Folders Unit Web Page](http://www.delphidabbler.com/software/shellfolders).