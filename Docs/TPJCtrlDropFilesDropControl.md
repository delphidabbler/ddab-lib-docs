# DropControl property #

**Project:** [Drop Files Components](DropFilesComponents.md).

**Unit:** _PJDropFiles_.

**Class:** _[TPJCtrlDropFiles](TPJCtrlDropFiles.md)_

```pascal
property DropControl: TControl;
```

## Description ##

Provides a reference to any control parented by the managed control that was under the mouse cursor when files were dropped. If no child controls were under the cursor then a reference to managed control itself is returned.