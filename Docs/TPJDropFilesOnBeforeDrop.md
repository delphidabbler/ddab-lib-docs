# OnBeforeDrop event #

**Project:** [Drop Files Components](DropFilesComponents.md).

**Unit:** _PJDropFiles_.

**Class:** _[TPJDropFiles](TPJDropFiles.md)_

```pascal
property OnBeforeDrop: TNotifyEvent;
```

## Description ##

This event is triggered when files are dropped on the control but before the files are processed. If the processing of files is likely to be a lengthy occurence then an hourglass or similar user interface device can be displayed here.

The _[Files](TPJDropFilesFiles.md)_ property does not yet contain details of the files dropped when this event is triggered, so the _Files_ property should not be read. The _[OnDropFiles](TPJDropFilesOnDropFiles.md)_ event is triggered after the processing of files takes place. The _Files_ property should therefore be read in the _OnDropFiles_ event handler.