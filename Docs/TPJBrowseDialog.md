# TPJBrowseDialog #

**Project:** [Shell Folders Unit](ShellFoldersUnit.md).

**Unit:** _PJShellFolders_.

This component permits the Windows _Browse for Folders_ dialog box to be displayed. _TPJBrowseDialog_ also enables the dialog box to be customised. The dialog box is displayed at run time when the _[Execute](TPJBrowseDialogExecute.md)_ method is called. The path and display name of the folder selected when the user OKs are made available via the component's properties.

## Methods ##

| **Method** | **Description** |
|:-----------|:----------------|
| _[Execute](TPJBrowseDialogExecute.md)_ | Displays the _Browse for Folders_ dialog. |

## Properties ##

| **Property** | **Description** |
|:-------------|:----------------|
| _[DisplayName](TPJBrowseDialogDisplayName.md)_ | Displays the name of the selected folder. |
| _[FolderName](TPJBrowseDialogFolderName.md)_ | Contains the path to the folder selected in the dialog box. |
| _[Handle](TPJBrowseDialogHandle.md)_ | The window handle of the dialog box. |
| _[Headline](TPJBrowseDialogHeadline.md)_ | Displays the given text in the Browse dialog box. |
| _[HelpContext](TPJBrowseDialogHelpContext.md)_ | Numeric ID for the components's context-sensitive help topic. |
| _[HelpKeyword](TPJBrowseDialogHelpKeyword.md)_ | Keyword for the component's context-sensitive help topic. |
| _[HelpType](TPJBrowseDialogHelpType.md)_ | Indicates whether the component's context sensitive help topic is identified by context ID or by keyword. |
| _[Options](TPJBrowseDialogOptions.md)_ | Determines the appearance and behavior of the _Browse for Folders_ dialog box. |
| _[RootFolderID](TPJBrowseDialogRootFolderID.md)_ | Determines the root folder displayed in the dialog box. |
| _[Title](TPJBrowseDialogTitle.md)_ | Specifies the text displayed in the dialog's title bar. |

## Events ##

| **Event** | **Description** |
|:----------|:----------------|
| _[OnClose](TPJBrowseDialogOnClose.md)_ | Triggered when the dialog closes. |
| _[OnHelp](TPJBrowseDialogOnHelp.md)_ | Triggered whenever help is requested from the browse for folders dialog box and is available. |
| _[OnInitialise](TPJBrowseDialogOnInitialise.md)_ | Triggered when the dialog initialises. |
| _[OnSelChange](TPJBrowseDialogOnSelChange.md)_ | Triggered whenever the selection in the dialog box changes. |
| _[OnSelChangeEx](TPJBrowseDialogOnSelChangeEx.md)_ | Triggered whenever the selection in the dialog box changes. |
| _[OnValidationFailed](TPJBrowseDialogOnValidationFailed.md)_ | Triggered whenever an invalid folder name is entered in the browse dialog's edit control and an attempt is made to close the dialog box. |