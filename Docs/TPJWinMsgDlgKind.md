# Kind property #

**Project:** [Message Dialogue Components](MessageDialogComponents.md).

**Unit:** _PJMessageDialog_.

**Class:** _[TPJWinMsgDlg](TPJWinMsgDlg.md)_

```pascal
type
  TPJMsgDlgKind = (
    mkWarning, mkInformation, mkQuery, mkError, mkUser,
    mkApplication, mkWinLogo, mkUnknown
  );

property Kind: TPJMsgDlgKind;
```

## Description ##

This property determines the appearance and other attributes of the dialogue box. The property specifies the icon that will appear in the dialogue box, the default window title and any sound played when the dialogue box is displayed. The default window title can be overridden using the _[Title](TPJWinMsgDlgTitle.md)_ property and sounds are only played when _[MakeSound](TPJWinMsgDlgMakeSound.md)_ is `True`.

The effect of each of the possible values of the _Kind_ property are described below:

| **Value** | **Icon** | **Default title** | **System Sound** |
|:----------|:---------|:------------------|:-----------------|
| `mkWarning` | System exclamation icon | "Warning" | `MB_ICONEXCLAMATION` |
| `mkInformation` | System information icon | "Information" | `MB_ICONASTERISK` |
| `mkQuery` | System confirmation icon | "Confirm" | `MB_ICONQUESTION` |
| `mkError` | System error icon | "Error" | `MB_ICONHAND` |
| `mkUser` | Specified by _[IconResource](TPJWinMsgDlgIconResource.md)_ property | Per _Application.Title_ property | `MB_OK` |
| `mkApplication` | System application icon | Per _Application.Title_ property | `MB_OK` |
| `mkWinLogo` | System Windows icon | Per _Application.Title_ property | `MB_OK` |
| `mkUnknown` | None | Per _Application.Title_ property | `MB_OK` |

Setting _Kind_ also updates the _[DlgType](TPJWinMsgDlgDlgType.md)_ property and vice versa. See the _[DlgType page](TPJWinMsgDlgDlgType.md)_ for full details.

**Notes:**

  1. When _Kind_ = `mkUser`, the icon is loaded from the resource specified by the _[IconResource](TPJWinMsgDlgIconResource.md)_ property.
  1. The appearance of system icons is operating system version dependent. On some Windows versions, the icon displayed for `mkApplication` and `mkWinLogo` is the same.
  1. Sounds are also operation system version and theme dependent. Some themes play no sound for some `MB_XXX` values.
  1. `mkUnknown` should not be selected explicitly. It is present to signal that an invalid dialogue kind has been specified when setting the _[DlgType](TPJWinMsgDlgDlgType.md)_ property.

The default value of the property is `mkInformation`.