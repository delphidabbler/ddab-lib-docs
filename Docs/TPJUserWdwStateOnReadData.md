# OnReadData event #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJUserWdwState](TPJUserWdwState.md)_

```pascal
type
  TPJWdwStateReadData = procedure(
    Sender: TObject; var Data: TPJWdwStateData
  ) of object;

property OnReadData: TPJWdwStateReadData;
```

## Description ##

_OnReadData_ is triggered when the component is about to restore the window's size, position and state and needs to retrieve saved window state data from persistent storage.

The user must handle this event by reading the required data from storage and storing the data in the fields of the _Data_ parameter, which is a _[TPJWdwStateData](TPJWdwStateData.md)_ record.

**See Also:**
> _[OnSaveData](TPJUserWdwStateOnSaveData.md)_ event.