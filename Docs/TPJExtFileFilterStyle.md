# Style property #

**Project:** [Drop Files Components](DropFilesComponents.md).

**Unit:** _PJDropFiles_.

**Class:** _[TPJExtFileFilter](TPJExtFileFilter.md)_

```pascal
property Style: TPJExtFileFilterStyle;
```

## Description ##

This property determines which kinds of file names have the extension filter applied. Possible values are given by the _[TPJExtFileFilterStyle](TPJExtFileFilterStyleEnum.md)_ enumeration.

The default value is `fsFilterFilesOnly`.

Note: To prevent files or folders passing through the filter being accepted by the drop files control, set the control's _Options_ property appropriately.