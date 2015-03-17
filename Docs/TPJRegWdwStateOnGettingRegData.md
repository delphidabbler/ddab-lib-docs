# OnGettingRegData event #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJRegWdwState](TPJRegWdwState.md)_

**Introduced:** v5.1

```pascal
type
  TPJWdwStateRegAccessEvent = procedure(
    const Reg: TRegistry
  ) of object;

property OnGettingRegData: TPJWdwStateRegAccessEvent;
```

## Description ##

_OnGettingRegData_ allows the user to read additional registry data when the component reads window state information.

The event is triggered just after the window's state information is read from the registry. The event makes available a reference to the _TRegistry_ object used to read the data. This object can be used to read any additional application defined information from the registry.

For example, the size of some controls that appear on the main form may be read. Such data will have been written using the _[OnPuttingRegData](TPJRegWdwStateOnPuttingRegData.md)_ **<sup>v5.1</sup>** event.