# OnGetRegData event #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJRegWdwState](TPJRegWdwState.md)_

```pascal
type
  TPJWdwStateGetRegData = procedure(
    var RootKey: HKEY; var SubKey: string
  ) of object;

property OnGetRegData: TPJWdwStateGetRegData;
```

## Description ##

This event is triggered just before the registry is read when restoring and saving a window. The current values of the _[RootKey](TPJRegWdwStateRootKey.md)_ and _[SubKey](TPJRegWdwStateSubKey.md)_ properties are passed as var parameters of the same name to the event handler, allowing the user to change the values, and hence the location within the registry where the window data is recorded.

Any value assigned to the _RootKey_ parameter must be a valid _HKEY_ or an exception will be raised. See the _[RootKey](TPJRegWdwStateRootKey.md)_ documentation for a list of valid values.

The purpose of the event is to enable the _[AutoSaveRestore](TPJCustomWdwStateAutoSaveRestore.md)_ property to be used without setting the _[RootKey](TPJRegWdwStateRootKey.md)_ and _[SubKey](TPJRegWdwStateSubKey.md)_ properties at design time  - i.e. handling the event allows either or both of the default _[RootKey](TPJRegWdwStateRootKey.md)_  and _[SubKey](TPJRegWdwStateSubKey.md)_ values to be overridden.

### Alternative Event ###

The _[OnGetRegDataEx](TPJRegWdwStateOnGetRegDataEx.md)_**<sup>v5.6</sup>** event provides an alternative way of to change the registry root- and sub-keys. It is similar to _OnGetRegData_ except that the root key is specified as one of the value from the _[TPJRegRootKey](TPJRegRootKey.md)_**<sup>v5.6</sup>** enumeration.

**Note:** You should choose which of _OnGetRegData_ and _[OnGetRegDataEx](TPJRegWdwStateOnGetRegDataEx.md)_**<sup>v5.6</sup>** to handle, but should not handle both events. If you do then _[OnGetRegDataEx](TPJRegWdwStateOnGetRegDataEx.md)_**<sup>v5.6</sup>** will be triggered and _OnGetRegData_ will be ignored.