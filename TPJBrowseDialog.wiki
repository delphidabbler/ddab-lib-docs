#summary TPJBrowseDialog class description
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= TPJBrowseDialog =

*Project:* [ShellFoldersUnit Shell Folders Unit].

*Unit:* _PJShellFolders_.

This component permits the Windows _Browse for Folders_ dialog box to be displayed. _TPJBrowseDialog_ also enables the dialog box to be customised. The dialog box is displayed at run time when the _[TPJBrowseDialogExecute Execute]_ method is called. The path and display name of the folder selected when the user OKs are made available via the component's properties.

== Methods ==

|| *Method* || *Description* ||
|| _[TPJBrowseDialogExecute Execute]_ || Displays the _Browse for Folders_ dialog. ||

== Properties ==

|| *Property* || *Description* ||
|| _[TPJBrowseDialogDisplayName DisplayName]_ || Displays the name of the selected folder. ||
|| _[TPJBrowseDialogFolderName FolderName]_ || Contains the path to the folder selected in the dialog box. ||
|| _[TPJBrowseDialogHandle Handle]_ || The window handle of the dialog box. ||
|| _[TPJBrowseDialogHeadline Headline]_ || Displays the given text in the Browse dialog box. ||
|| _[TPJBrowseDialogHelpContext HelpContext]_ || Numeric ID for the components's context-sensitive help topic. ||
|| _[TPJBrowseDialogHelpKeyword HelpKeyword]_ || Keyword for the component's context-sensitive help topic. ||
|| _[TPJBrowseDialogHelpType HelpType]_ || Indicates whether the component's context sensitive help topic is identified by context ID or by keyword. ||
|| _[TPJBrowseDialogOptions Options]_ || Determines the appearance and behavior of the _Browse for Folders_ dialog box. ||
|| _[TPJBrowseDialogRootFolderID RootFolderID]_ || Determines the root folder displayed in the dialog box. ||
|| _[TPJBrowseDialogTitle Title]_ || Specifies the text displayed in the dialog's title bar. ||

== Events ==

|| *Event* || *Description* ||
|| _[TPJBrowseDialogOnClose OnClose]_ || Triggered when the dialog closes. ||
|| _[TPJBrowseDialogOnHelp OnHelp]_ || Triggered whenever help is requested from the browse for folders dialog box and is available. ||
|| _[TPJBrowseDialogOnInitialise OnInitialise]_ || Triggered when the dialog initialises. ||
|| _[TPJBrowseDialogOnSelChange OnSelChange]_ || Triggered whenever the selection in the dialog box changes. ||
|| _[TPJBrowseDialogOnSelChangeEx OnSelChangeEx]_ || Triggered whenever the selection in the dialog box changes. ||
|| _[TPJBrowseDialogOnValidationFailed OnValidationFailed]_ || Triggered whenever an invalid folder name is entered in the browse dialog's edit control and an attempt is made to close the dialog box. ||
