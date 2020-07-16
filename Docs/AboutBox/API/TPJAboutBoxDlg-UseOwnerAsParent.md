# UseOwnerAsParent property

**Project:** [About Box Component](../API.md)

**Unit:** _PJAbout_.

**Class:** [_TPJAboutBoxDlg_](./TPJAboutBoxDlg.md)

```pascal
property UseOwnerAsParent: Boolean;
```

## Description

When true this property sets the dialog box's parent to be the window handle of the control that owns the dialog box, providing the owner has a window handle.

The property is provided for when the application's main form, rather than the hidden application window is displayed in the Windows task bar. If this property is not set true it may be possible, depending on the compiler used, for the main window to be brought to the front by clicking its task bar icon, hiding the dialog box and hence freezing the program.

The default value is _False_.
