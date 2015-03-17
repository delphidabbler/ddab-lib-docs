# DlgType property #

**Project:** [Message Dialogue Components](MessageDialogComponents.md).

**Unit:** _PJMessageDialog_.

**Class:** _[TPJWinMsgDlg](TPJWinMsgDlg.md)_

```pascal
property DlgType: LongWord;
```

## Description ##

This property provides an alternative method to setting the _[ButtonGroup](TPJWinMsgDlgButtonGroup.md)_ and _[Kind](TPJWinMsgDlgKind.md)_ properties using a subset of the constants used to customise the _MessageBox_ Windows API function via its _uType_ parameter. However, not all the API flags are supported.

_DlgType_ is never stored in a form file - it's value is determined by the _[ButtonGroup](TPJWinMsgDlgButtonGroup.md)_ and _[Kind](TPJWinMsgDlgKind.md)_ property values and whether a help button is displayed. Changing any of these values modifies the value of _DlgType_. Conversely, setting _DlgType_ updates both the _[ButtonGroup](TPJWinMsgDlgButtonGroup.md)_ and _[Kind](TPJWinMsgDlgKind.md)_ properties.

Often the value of _DlgType_ will change as soon as it is set because of the presence of any unsupported values, whether a help button is displayed or if a required value has not been provided.

Reading and writing the property are dealt with separately below.

### Setting _DlgType_ ###

_DlgType_ supports a combination of various categories of constants that are ORd together.

#### Button Group ####

The buttons displayed in the dialogue box can be determined by specifying one, and only one, of the following constants. Setting one of these values also updates the _[ButtonGroup](TPJWinMsgDlgButtonGroup.md)_ property.

| **Constant** | **Buttons Displayed** | **New _ButtonGroup_ Value** |
|:-------------|:----------------------|:----------------------------|
| `MB_OK` | A single OK button | `bgOK` |
| `MB_OKCANCEL` | OK and Cancel | `bgOKCancel` |
| `MB_ABORTRETRYIGNORE` | Abort, Retry and Cancel | `bgAbortRetryIgnore` |
| `MB_YESNOCANCEL` | Yes, No and Cancel | `bgYesNoCancel` |
| `MB_YESNO` | Yes and No | `bgYesNo` |
| `MB_RETRYCANCEL` | Retry and Cancel | `bgRetryCancel` |
| `MB_CANCELTRYCONTINUE` | Cancel, Try Again and Continue | `bgCancelTryContinue` |

If any other value in the range `$00000000` to `$0000000F` is specified then _[ButtonGroup](TPJWinMsgDlgButtonGroup.md)_ is set to `bgUnknown` and the value in _DlgType_ is replaced by `UNKNOWN_BUTTONGROUP` (defined in _PJMessageDialog.pas_). To check for an unknown or invalid button group first set _DlgType_ then perform the following test:

```pascal
begin
  if PJWinMsgDlg1.DlgType and MB_TYPEMASK = UNKNOWN_BUTTONGROUP then
    // button group unknown or unsupported
end;
```

#### Dialogue Kind ####

The kind of dialogue box (its icon, default title, etc.) is specified by ORing one of the following constants with one of those used to determine the button group. Setting one of these values updates the _[Kind](TPJWinMsgDlgKind.md)_ property.

| **Constant** | **Icon used** | **Default Title** | **New _Kind_ Value** |
|:-------------|:--------------|:------------------|:---------------------|
| `MB_ICONEXCLAMATION` | System exclamation icon | "Warning" | `mkWarning` |
| `MB_ICONWARNING` | System exclamation icon | "Warning" | `mkWarning` |
| `MB_ICONINFORMATION` | System information icon | "Information" | `mkInformation` |
| `MB_ICONASTERISK` | System information icon | "Information" | `mkInformation` |
| `MB_ICONQUESTION` | System confirmation icon | "Confirm" | `mkQuery` |
| `MB_ICONSTOP` | System error icon | "Error" | `mkError` |
| `MB_ICONERROR` | System error icon | "Error" | `mkError` |
| `MB_ICONHAND` | System error icon | "Error" | `mkError` |
| `MB_USERICON` | Per _[IconResource](TPJWinMsgDlgIconResource.md)_ property | Per _Application.Title_ property | `mkUser` |

If any other value in the range `$00000010` to `$000000F0` is specified then _[Kind](TPJWinMsgDlgKind.md)_ is set to `mkUnknown` and the value in _DlgType_ is replaced by `UNKNOWN_ICON` (defined in _PJMessageDialog.pas_). To check for an unknown or invalid dialogue kind first set _DlgType_ then perform the following test:

```pascal
begin
  if PJWinMsgDlg1.DlgType and MB_ICONMASK = UNKNOWN_ICON then
    // dialogue kind unknown or not supported
end;
```

#### Help Button ####

In the standard Windows API call specifying `MB_HELP` causes a help button to be displayed. However, _[TPJWinMsgDlg](TPJWinMsgDlg.md)_ only displays a help button when the _[HelpContext](TPJWinMsgDlgHelpContext.md)_ property is non-zero, so supporting `MB_HELP` would break the component's normal behaviour. Consequently if _DlgType_ is set to a value that includes `MB_HELP`, the flag is ignored.

Note though that `MB_HELP` may be included in _DlgType_ when it is read, depending on if a Help button will be displayed. See below for details.

### Reading _DlgType_ ###

The value returned when _DlgType_ is read does not directly relate to the value set. This is because the value of _DlgType_ is not stored and its value when read is calculated from the values of various other properties. Consequently any unsupported flags are stripped away. Furthermore _DlgType_ introduces some new flags to indicate errors.

Factors that determine the value of _DlgType_ are:

  1. The _[ButtonGroup](TPJWinMsgDlgButtonGroup.md)_ property.
  1. The _[Kind](TPJWinMsgDlgKind.md)_ property.
  1. Whether a help button will be displayed by the dialogue.

Each of these factors is discussed separately below.

#### Button Group ####

The button group component of _DlgType_ is set according to the value of the _[ButtonGroup](TPJWinMsgDlgButtonGroup.md)_ property as per the following table:

| **_ButtonGroup_ Value** | **Flag included in _DlgType_** |
|:------------------------|:-------------------------------|
| `bgAbortRetryIgnore` | `MB_ABORTRETRYIGNORE` |
| `bgOK` | `MB_OK` |
| `bgOKCancel` | `MB_OKCANCEL` |
| `bgRetryCancel` | `MB_RETRYCANCEL` |
| `bgYesNo` | `MB_YESNO` |
| `bgYesNoCancel` | `MB_YESNOCANCEL` |
| `bgUnknown` | `UNKNOWN_BUTTONGROUP` |
| `bgCancelTryContinue` | `MB_CANCELTRYCONTINUE` |

`UNKNOWN_BUTTONGROUP` and `MB_CANCELTRYCONTINUE` are both defined in the _PJMessageDialog_ unit and the remaining values are defined in the _Windows_ unit.

The button group values are ORd with other values stored in _DlgType_. To extract them AND the value of _DlgType_ with `MB_TYPEMASK`. E.g.

```pascal
var
  BG: LongWord;
begin
  BG := PJWinMsgDlg1.DlgType and MB_TYPEMASK;
end;
```

#### Dialogue Kind ####

The component of _DlgType_ that identifies the kind of dialogue box displayed is set according to the value of the _[Kind](TPJWinMsgDlgKind.md)_ property as per the following table:

| **_Kind_ Value** | **Flag included in _DlgType_** |
|:-----------------|:-------------------------------|
| `mkWarning` | `MB_ICONWARNING` |
| `mkInformation` | `MB_ICONINFORMATION` |
| `mkQuery` | `MB_ICONQUESTION` |
| `mkError` | `MB_ICONERROR` |
| `mkUser` | `MB_USERICON` |
| `mkApplication` | `UNKNOWN_ICON` |
| `mkWinLogo` | `UNKNOWN_ICON` |
| `mkUnknown` | `UNKNOWN_ICON` |

`UNKNOWN_ICON` is defined in the _PJMessageDialog_ unit. Note that `mkWinLogo` and `mkApplication` have no equivalent in the _MessageBox_ API function and are therefore flagged as unknown.

The dialogue kind values are ORd with other values stored in _DlgType_. To extract them AND the value of _DlgType_ with `MB_ICONMASK`. E.g.

```pascal
var
  K: LongWord;
begin
  K := PJWinMsgDlg1.DlgType and MB_ICONMASK;
end;
```

#### Help Button ####

If the dialogue box will show a help button (which is the case if and only if _[HelpContext](TPJWinMsgDlgHelpContext.md)_ is non zero) then `MB_HELP` is included in _DlgType_. Check for the presence of `MB_HELP` like this:

```pascal
begin
  if PJWinMsgDlg1.DlgType and MB_HELP = MB_HELP then
    // MB_HELP present
end;
```