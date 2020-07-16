# ButtonPlacing property

**Project:** [About Box Component](../API.md)

**Unit:** _PJAbout_.

**Class:** [_TPJAboutBoxDlg_](./TPJAboutBoxDlg.md)

```pascal
property ButtonPlacing: TPJAboutBtnPlacing;

type TPJAboutBtnPlacing = (abpLeft, abpCentre, abpRight);
```

## Description

The About box contains one button which is used to close the dialog box. The button is positioned at the bottom of the dialog box, but can be aligned left, centre or right. The _ButtonPlacing_ property is used to determine which position the button occupies. Valid values for the property and their meanings are as follows:

|   Value   |   Meaning   |
|-----------|-------------|
| _abpLeft_ | Display the button at the bottom left of the dialog box. |
| _abpCentre_ | Display the button at the bottom centre  of the dialog box. |
| _abpRight_ | Display the button at the bottom right of the dialog box. |

The default value is _abpCentre_.
