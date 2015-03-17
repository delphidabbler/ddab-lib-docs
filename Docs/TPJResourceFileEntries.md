# Entries property #

**Project:** [Resource File Unit](ResFileUnit.md)

**Unit:** _PJResFile_.

**Class:** _[TPJResourceFile](TPJResourceFile.md)_

```pascal
property Entries[Idx: Integer]: TPJResourceEntry;
```

This read-only property provides indexed access to all the resources in the resource file. Valid indices are in the range 0 to _[EntryCount](TPJResourceFileEntryCount.md)_ - 1.