# TPJAboutBoxDlg class

**Project:** [About Box Component](../API.md).

**Unit:** _PJAbout_.

This non-visual component encapsulates an About Box in a non-visual component. It is displayed by calling its [_Execute_](./TPJAboutBoxDlg-Execute.md) method. It has string properties to display five different pieces of information in the about box. They are: [_Copyright_](./TPJAboutBoxDlg-Copyright.md), [_Notes_](./TPJAboutBoxDlg-Notes.md), [_ProgramName_](./TPJAboutBoxDlg-ProgramName.md), [_Title_](./TPJAboutBoxDlg-Title.md) and [_Version_](./TPJAboutBoxDlg-Version.md).

Alternatively, the about box can display information from a _VERSIONINFO_ resource included in a program file. This is achieved by setting the [_VersionInfo_](./TPJAboutBoxDlg-VersionInfo.md) property to reference a [_TPJVersionInfo_](../../VerInfo/API/TPJVersionInfo.md) component which extracts the required version information from an executable file.

The application's icon is displayed in the dialog box. This is the icon specified by the _Icon_ property of the _TApplication_ object. If no icon has been specified for the application then default Delphi icon is used.

Other properties are used to position of the about box on the screen and control the position and appearance of the dialog's _Close_ button.

The [_HelpContext_](./TPJAboutBoxDlg-HelpContext.md) property allows Windows Help to be displayed for the dialog box when the F1 key is pressed.

## Methods

| Method | Description |
|--------|-------------|
| [_Execute_](./TPJAboutBoxDlg-Execute.md) | Displays the about box. |

## Properties

| Property | Description |
|----------|-------------|
| [_ButtonGlyph_](./TPJAboutBoxDlg-ButtonGlyph.md) | Determines which, if any, glyph is displayed on the dialog's close button. |
| [_ButtonHeight_](./TPJAboutBoxDlg-ButtonHeight.md) | Specifies the height of the dialog's close button. |
| [_ButtonKind_](./TPJAboutBoxDlg-ButtonKind.md) | Determines the text displayed on the dialog's close button. |
| [_ButtonPlacing_](./TPJAboutBoxDlg-ButtonPlacing.md) | Determines the horizontal alignment of the dialog's close button. |
| [_ButtonWidth_](./TPJAboutBoxDlg-ButtonWidth.md) | Specifies the width of the dialog's close button. |
| [_CentreDlg_](./TPJAboutBoxDlg-CentreDlg.md) | Determines whether or not the dialog box is centred on screen. |
| [_Copyright_](./TPJAboutBoxDlg-Copyright.md) | The copyright message displayed in the about box. |
| [_DlgLeft_](./TPJAboutBoxDlg-DlgLeft.md) | Specifies the location of the left hand side of the about box. |
| [_DlgTop_](./TPJAboutBoxDlg-DlgTop.md) | Specifies the location of the top of the about box. |
| [_Font_](./TPJAboutBoxDlg-Font.md) | Specifies the font used in the dialog box. |
| [_HelpContext_](./TPJAboutBoxDlg-HelpContext.md) | Stores the help topic number accessed when F1 is pressed. A zero value is ignored. |
| [_Notes_](./TPJAboutBoxDlg-Notes.md) | Notes displayed in the dialog box. |
| [_Position_](./TPJAboutBoxDlg-Position.md) | Determines whether the about box is positioned relative to screen, desktop or owner form. |
| [_ProgramName_](./TPJAboutBoxDlg-ProgramName.md) | Name of the program displayed in the about box. |
| [_Title_](./TPJAboutBoxDlg-Title.md) | Text displayed in the caption of the dialog box window. |
| [_UseOSStdFonts_](./TPJAboutBoxDlg-UseOSStdFonts.md) | Specifies whether the dialog box should use the system's default font. |
| [_UseOwnerAsParent_](./TPJAboutBoxDlg-UseOwnerAsParent.md) | Determines if the dialog box should to be forced to be a child window of any owning control. |
| [_Version_](./TPJAboutBoxDlg-Version.md) | The version number information to be displayed in the dialog box. |
| [_VersionInfo_](./TPJAboutBoxDlg-VersionInfo.md) | Reference to any [_TPJVersionInfo_](../../VerInfo/API/TPJVersionInfo.md) component that provides the text displayed in the about box. |

## Events

_TPJAboutBoxDlg_ defines no events.
