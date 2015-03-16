<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# TPJAboutBoxDlg #

**Project:** [About Box Component](AboutBoxComponent.md).

**Unit:** _PJAbout_.

This non-visual component encapsulates an About Box in a non-visual component. It is displayed by calling its _[Execute](TPJAboutBoxDlgExecute.md)_ method. It has string properties to display five different pieces of information in the about box. They are: _[Copyright](TPJAboutBoxDlgCopyright.md)_, _[DlgNotes](TPJAboutBoxDlgNotes.md)_, _[ProgramName](TPJAboutBoxDlgProgramName.md)_, _[Title](TPJAboutBoxDlgTitle.md)_ and _[Version](TPJAboutBoxDlgVersion.md)_.

Alternatively, the about box can display information from a _VERSIONINFO_ resource included in a program file. This is achieved by setting the _[VersionInfo](TPJAboutBoxDlgVersionInfo.md)_ property to reference a _[TPJVersionInfo](TPJVersionInfo.md)_ component which extracts the required version information from an executable file.

The application's icon is displayed in the dialog box. This is the icon specified by the _Icon_ property of the _TApplication_ object. If no icon has been specified for the application then default Delphi icon is used.

Other properties are used to position of the about box on the screen and control the position and appearance of the dialog's _Close_ button.

The _[HelpContext](TPJAboutBoxDlgHelpContext.md)_ property allows Windows Help to be displayed for the dialog box when the F1 key is pressed.

## Methods ##

| **Method** | **Description** |
|:-----------|:----------------|
| _[Execute](TPJAboutBoxDlgExecute.md)_ | Displays the about box. |

## Properties ##

| **Property** | **Description** |
|:-------------|:----------------|
| _~~AutoDetectGlyphs~~_ | **Removed in v3.6**<br>Determines whether the display of glyphs depends on the <i>ButtonGlyph</i> property or depends on the default compiler settings.<br><i>This property was deprecated in v3.5.</i> <br>
<tr><td> <i><a href='TPJAboutBoxDlgButtonGlyph.md'>ButtonGlyph</a></i> </td><td> Determines which, if any, glyph is displayed on the dialog's close button. </td></tr>
<tr><td> <i><a href='TPJAboutBoxDlgButtonHeight.md'>ButtonHeight</a></i> </td><td> Specifies the height of the dialog's close button. </td></tr>
<tr><td> <i><a href='TPJAboutBoxDlgButtonKind.md'>ButtonKind</a></i> </td><td> Determines the text displayed on the dialog's close button. </td></tr>
<tr><td> <i><a href='TPJAboutBoxDlgButtonPlacing.md'>ButtonPlacing</a></i> </td><td> Determines the horizontal alignment of the dialog's close button. </td></tr>
<tr><td> <i><a href='TPJAboutBoxDlgButtonWidth.md'>ButtonWidth</a></i> </td><td> Specifies the width of the dialog's close button. </td></tr>
<tr><td> <i><a href='TPJAboutBoxDlgCentreDlg.md'>CentreDlg</a></i> </td><td> Determines whether or not the dialog box is centred on screen. </td></tr>
<tr><td> <i><a href='TPJAboutBoxDlgCopyright.md'>Copyright</a></i> </td><td> The copyright message displayed in the about box. </td></tr>
<tr><td> <i><a href='TPJAboutBoxDlgDlgLeft.md'>DlgLeft</a></i> </td><td> Specifies the location of the left hand side of the about box. </td></tr>
<tr><td> <i><a href='TPJAboutBoxDlgDlgTop.md'>DlgTop</a></i> </td><td> Specifies the location of the top of the about box. </td></tr>
<tr><td> <i><a href='TPJAboutBoxDlgFont.md'>Font</a></i> </td><td> Specifies the font used in the dialog box. </td></tr>
<tr><td> <i><a href='TPJAboutBoxDlgHelpContext.md'>HelpContext</a></i> </td><td> Stores the help topic number accessed when F1 is pressed. A zero value is ignored. </td></tr>
<tr><td> <i><a href='TPJAboutBoxDlgNotes.md'>Notes</a></i> </td><td> Notes displayed in the dialog box. </td></tr>
<tr><td> <i><a href='TPJAboutBoxDlgPosition.md'>Position</a></i> </td><td> Determines whether the about box is positioned relative to screen, desktop or owner form. </td></tr>
<tr><td> <i><a href='TPJAboutBoxDlgProgramName.md'>ProgramName</a></i> </td><td> Name of the program displayed in the about box. </td></tr>
<tr><td> <i><a href='TPJAboutBoxDlgTitle.md'>Title</a></i> </td><td> Text displayed in the caption of the dialog box window. </td></tr>
<tr><td> <i><a href='TPJAboutBoxDlgUseOSStdFonts.md'>UseOSStdFonts</a></i> </td><td> Specifies whether the dialog box should use the system's default font. </td></tr>
<tr><td> <i><a href='TPJAboutBoxDlgUseOwnerAsParent.md'>UseOwnerAsParent</a></i> </td><td> Determines if the dialog box should to be forced to be a child window of any owning control. </td></tr>
<tr><td> <i><a href='TPJAboutBoxDlgVersion.md'>Version</a></i> </td><td> The version number information to be displayed in the dialog box. </td></tr>
<tr><td> <i><a href='TPJAboutBoxDlgVersionInfo.md'>VersionInfo</a></i> </td><td> Reference to any <i><a href='TPJVersionInfo.md'>TPJVersionInfo</a></i> component that provides the text displayed in the about box. </td></tr></tbody></table>

## Events ##

_TPJAboutBoxDlg_ defines no events.