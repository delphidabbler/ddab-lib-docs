# TPJSpecialFolderInfo #

**Project:** [Shell Folders Unit](ShellFoldersUnit.md).

**Unit:** _PJShellFolders_.

_TPJSpecialFolderInfo_ is a non-visual component that provides information about a Windows special folders.

To get information about a special folder set the _[FolderID](TPJSpecialFolderInfoFolderID.md)_ property to the required special folder id. The run time only properties of the component can then be used to read off information about the folder. Test _[IsSupported](TPJSpecialFolderInfoIsSupported.md)_ to check if the folder is supported on the current platform. If the folder is not supported then both _[Path](TPJSpecialFolderInfoPath.md)_ and _[DisplayName](TPJSpecialFolderInfoDisplayName.md)_ are empty. If _[IsVirtual](TPJSpecialFolderInfoIsVirtual.md)_ is true then the folder is virtual and the Path property will be empty. If _[IsVirtual](TPJSpecialFolderInfoIsVirtual.md)_ is false then the folder exists in the file system and the folder's path is given by the _[Path](TPJSpecialFolderInfoPath.md)_ property. _[DisplayName](TPJSpecialFolderInfoDisplayName.md)_ gives the name used for the folder - for non-virtual folders this often has the same value as _[Path](TPJSpecialFolderInfoPath.md)_.

## Supporting functions ##

Valid values for _[FolderID](TPJSpecialFolderInfoFolderID.md)_ can be obtained using the _[TPJSpecialFolderEnum](TPJSpecialFolderEnum.md)_ class. Supplying invalid values to _[FolderID](TPJSpecialFolderInfoFolderID.md)_ will cause an exception to be raised. Use the _[IsValidSpecialFolderId](PJShellFoldersFunctions.md#isvalidspecialfolderid)_ function to check validity. _[SpecialFolderIdToStr](PJShellFoldersFunctions.md#specialfolderidtostr)_ returns the identifier of a valid folder ID.

## Methods ##

_TPJSpecialFolderInfo_ defines no new methods.

## Properties ##

| **Property** | **Description** |
|:-------------|:----------------|
| _[DisplayName](TPJSpecialFolderInfoDisplayName.md)_ | This property gives the name used to display the folder in Explorer. |
| _[FolderID](TPJSpecialFolderInfoFolderID.md)_ | Use this property to provide the folder ID of the special folder. |
| _[IsSupported](TPJSpecialFolderInfoIsSupported.md)_ | Use this property to determine if the current special folder is supported by the operating system. |
| _[IsVirtual](TPJSpecialFolderInfoIsVirtual.md)_ | Use this property to determine if the current special folder is virtual. |
| _[Path](TPJSpecialFolderInfoPath.md)_ | This property specifies the location of the folder in the file system, if any. |

## Events ##

_TPJSpecialFolderInfo_ defines no new events.
