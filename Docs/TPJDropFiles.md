# TPJDropFiles #

**Project:** [Drop Files Components](DropFilesComponents.md).

**Unit:** _PJDropFiles_.

This component provides a window which can accept files dragged and dropped from Windows Explorer (the component handles `WM_DROPFILES` messages to do this). This control can contain child components (in a similar way to _TPanel_ components). Files dropped over any such child component are also accepted by the parent _TPJDropFiles_ component.

The main use for _TPJDropFiles_ is when you need to detect file drops on non-windowed components such as _TLabel_ or _TShape_. To do this drop a _TPJDropFiles_ on a form and then place the required non-windowed control on top of the _TPJDropFiles_, aligning and sizing both components as required.

## Methods ##

| **Method** | **Description** |
|:-----------|:----------------|
| _[Paint](TPJDropFilesPaint.md)_ | Paints the outline of the component at design time. Does nothing at run time. |

## Properties ##

| **Property** | **Description** |
|:-------------|:----------------|
| _Align_ | Inherited from _TCustomControl_. See Delphi help for details. |
| _Anchor_ | Inherited from _TCustomControl_. See Delphi help for details. |
| _Constraints_ | Inherited from _TCustomControl_. See Delphi help for details. |
| _[Count](TPJDropFilesCount.md)_ | This read-only property returns the number of files dropped on the control. |
| _Cursor_ | Inherited from _TCustomControl_. See Delphi help for details. |
| _[DropControl](TPJDropFilesDropControl.md)_ | This read only property references the control that the files were dropped on. |
| _[DropPoint](TPJDropFilesDropPoint.md)_ | This read only property gives the mouse coordinates where the files were dropped. |
| _[Enabled](TPJDropFilesEnabled.md)_ | Inherited from _TCustomControl_. See Delphi help for details. |
| _[FileName](TPJDropFilesFileName.md)_ | The name of the file dropped on the control. |
| _[Files](TPJDropFilesFiles.md)_ | The names of the most recent files dropped on the control. |
| _[Filter](TPJDropFilesFilter.md)_ | References a file filter component used to filter the names of dropped files. |
| _[ForegroundOnDrop](TPJDropFilesForegroundOnDrop.md)_ | Causes the owning window to be brought to front when files are dropped. |
| _Height_ | Inherited from _TCustomControl_. See Delphi help for details. |
| _HelpContext_ | Inherited from _TCustomControl_. See Delphi help for details. |
| _HelpKeyword_ | Inherited from _TCustomControl_. See Delphi help for details. |
| _HelpType_ | Inherited from _TCustomControl_. See Delphi help for details. |
| _Hint_ | Inherited from _TCustomControl_. See Delphi help for details. |
| _[IsFolder](TPJDropFilesIsFolder.md)_ | Tells whether each of the dropped files is a folder or a file. |
| _Left_ | Inherited from _TCustomControl_. See Delphi help for details. |
| _Name_ | Inherited from _TCustomControl_. See Delphi help for details. |
| _[Options](TPJDropFilesOptions.md)_ | Determines how the dropped files are processed and which files are stored in the _[Files](TPJDropFilesFiles.md)_ property. |
| _ParentShowHint_ | Inherited from _TCustomControl_. See Delphi help for details. |
| _[PassThrough](TPJDropFilesPassThrough.md)_ | Causes drop files messages to be passed through to the owning form. |
| _ShowHint_ | Inherited from _TCustomControl_. See Delphi help for details. |
| _TabOrder_ | Inherited from _TCustomControl_. See Delphi help for details. |
| _TabStop_ | Inherited from _TCustomControl_. See Delphi help for details. |
| _Tag_ | Inherited from _TCustomControl_. See Delphi help for details. |
| _Top_ | Inherited from _TCustomControl_. See Delphi help for details. |
| _Visible_ | Inherited from _TCustomControl_. See Delphi help for details. |
| _Width_ | Inherited from _TCustomControl_. See Delphi help for details. |

## Events ##

| **Event** | **Description** |
|:----------|:----------------|
| _[OnBeforeDrop](TPJDropFilesOnBeforeDrop.md)_ | Event that occurs just before files dropped on the control are processed. |
| _[OnDropFiles](TPJDropFilesOnDropFiles.md)_ | Event that occurs when files are dropped on the component's window. |
| _[OnFileFilter](TPJDropFilesOnFileFilter.md)_ | Event that occurs for each file and folder processed and allows for custom filtering of files. |