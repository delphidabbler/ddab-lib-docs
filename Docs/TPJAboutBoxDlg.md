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

| Method | Description |
| ------ | ----------- |
| _[Execute](TPJAboutBoxDlgExecute.md)_ | Displays the about box. |

## Properties ##

| Property | Description |
| -------- | ----------- |
| _~~AutoDetectGlyphs~~_ | **Removed in v3.6**<br>Determines whether the display of glyphs depends on the _[ButtonGlyph](TPJAboutBoxDlgButtonGlyph.md)_ property or depends on the default compiler settings.<br>_This property was deprecated in v3.5._ |
| _[ButtonGlyph](TPJAboutBoxDlgButtonGlyph.md)_ | Determines which, if any, glyph is displayed on the dialog's close button. |
| _[ButtonHeight](TPJAboutBoxDlgButtonHeight.md)_ | Specifies the height of the dialog's close button. |
| _[ButtonKind](TPJAboutBoxDlgButtonKind.md)_ | Determines the text displayed on the dialog's close button. |
| _[ButtonPlacing](TPJAboutBoxDlgButtonPlacing.md)_ | Determines the horizontal alignment of the dialog's close button. |
| _[ButtonWidth](TPJAboutBoxDlgButtonWidth.md)_ | Specifies the width of the dialog's close button. |
| _[CentreDlg](TPJAboutBoxDlgCentreDlg.md)_ | Determines whether or not the dialog box is centred on screen. |
| _[Copyright](TPJAboutBoxDlgCopyright.md)_ | The copyright message displayed in the about box. |
| _[DlgLeft](TPJAboutBoxDlgDlgLeft.md)_ | Specifies the location of the left hand side of the about box. |
| _[DlgTop](TPJAboutBoxDlgDlgTop.md)_ | Specifies the location of the top of the about box. |
| _[Font](TPJAboutBoxDlgFont.md)_ | Specifies the font used in the dialog box. |
| _[HelpContext](TPJAboutBoxDlgHelpContext.md)_ | Stores the help topic number accessed when F1 is pressed. A zero value is ignored. |
| _[Notes](TPJAboutBoxDlgNotes.md)_ | Notes displayed in the dialog box. |
| _[Position](TPJAboutBoxDlgPosition.md)_ | Determines whether the about box is positioned relative to screen, desktop or owner form. |
| _[ProgramName](TPJAboutBoxDlgProgramName.md)_ | Name of the program displayed in the about box. |
| _[Title](TPJAboutBoxDlgTitle.md)_ | Text displayed in the caption of the dialog box window. |
| _[UseOSStdFonts](TPJAboutBoxDlgUseOSStdFonts.md)_ | Specifies whether the dialog box should use the system's default font. |
| _[UseOwnerAsParent](TPJAboutBoxDlgUseOwnerAsParent.md)_ | Determines if the dialog box should to be forced to be a child window of any owning control. |
| _[Version](TPJAboutBoxDlgVersion.md)_ | The version number information to be displayed in the dialog box. |
| _[VersionInfo](TPJAboutBoxDlgVersionInfo.md)_ | Reference to any _[TPJVersionInfo](TPJVersionInfo.md)_ component that provides the text displayed in the about box. |

## Events ##

_TPJAboutBoxDlg_ defines no events.