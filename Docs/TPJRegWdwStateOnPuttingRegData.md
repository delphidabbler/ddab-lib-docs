# OnPuttingRegData event #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJRegWdwState](TPJRegWdwState.md)_

**Introduced:** v5.1

```pascal
type
  TPJWdwStateRegAccessEvent = procedure(
    const Reg: TRegistry
  ) of object;

property OnPuttingRegData: TPJWdwStateRegAccessEvent;
```

## Description ##

_OnPuttingRegData_ allows user to write additional registry data when the component writes window state information.

The event is triggered just after the window's state information is written to the registry. The event makes available a reference to the _TRegistry_ object used to write the data. This object can be used to write any additional application defined information to the registry.

For example, the size of some controls that appear on the main form may be written. Such data can be read again using the _[OnGettingRegData](TPJRegWdwStateOnGettingRegData.md)_ **<sup>v5.1</sup>** event.