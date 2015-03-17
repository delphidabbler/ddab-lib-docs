# TPJFormDropFiles #

**Project:** [Drop Files Components](DropFilesComponents.md).

**Unit:** _PJDropFiles_.

This non-visual component catches all `WM_DROPFILES` messages that are received by the form where it is placed. The component therefore intercepts files dragged from Windows Explorer and dropped anywhere on the form, including the non-client areas. Use _TPJFormDropFiles_ whenever you just need to catch files anywhere on the main window without bothering about which particular control the files are dropped on.

## Methods ##

_TPJFormDropFiles_ defines no new methods.

## Properties ##

| **Property** | **Description** |
|:-------------|:----------------|
| _[Count](TPJFormDropFilesCount.md)_ | This read-only property returns the number of files dropped on the form. |
| _[DropControl](TPJFormDropFilesDropControl.md)_ | This read only property references any control on the form that the files were dropped on. |
| _[DropPoint](TPJFormDropFilesDropPoint.md)_ | This read only property gives the mouse coordinates where the files were dropped. |
| _[Enabled](TPJFormDropFilesEnabled.md)_ | Determines whether dropped files are handled or ignored. |
| _[FileName](TPJFormDropFilesFileName.md)_ | The name of a file dropped on the form. |
| _[Files](TPJFormDropFilesFiles.md)_ | The names of the most recent files dropped on the form. |
| _[Filter](TPJFormDropFilesFilter.md)_ | References a file filter component used to filter the names of dropped files. |
| _[ForegroundOnDrop](TPJFormDropFilesForegroundOnDrop.md)_ | Causes the form to be brought to the front when files are dropped. |
| _[IsFolder](TPJFormDropFilesIsFolder.md)_ | Tells whether each of the dropped files is a folder or a file. |
| _Name_ | Inherited from _TComponent_. See Delphi help for details. |
| _[Options](TPJFormDropFilesOptions.md)_ | Determines how the dropped files are processed and which files are stored in the _[Files](TPJFormDropFilesFiles.md)_ property. |
| _Tag_ | Inherited from _TComponent_. See Delphi help for details. |

## Events ##

| **Event** | **Description** |
|:----------|:----------------|
| _[OnBeforeDrop](TPJFormDropFilesOnBeforeDrop.md)_ | Event that occurs just before files dropped on the form are processed. |
| _[OnDropFiles](TPJFormDropFilesOnDropFiles.md)_ | Event that occurs when files are dropped on the form. |
| _[OnFileFilter](TPJFormDropFilesOnFileFilter.md)_ | Event that occurs for each file and folder processed and allows for custom filtering of files. |