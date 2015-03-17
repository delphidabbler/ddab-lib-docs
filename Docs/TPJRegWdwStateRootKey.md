# RootKey property #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJRegWdwState](TPJRegWdwState.md)_

```pascal
property RootKey: HKEY;
```

## Description ##

This property allows the user to specify the registry root key under which the window size, position and state information is recorded. The information is saved in a subkey of this root key determined by the _[SubKey](TPJRegWdwStateSubKey.md)_ property. If _RootKey_ is set to an invalid _HKEY_ value an exception is raised. Valid values are:

```pascal
HKEY_CLASSES_ROOT     = $80000000;
HKEY_CURRENT_USER     = $80000001;
HKEY_LOCAL_MACHINE    = $80000002;
HKEY_USERS            = $80000003;
HKEY_PERFORMANCE_DATA = $80000004;
HKEY_CURRENT_CONFIG   = $80000005;
HKEY_DYN_DATA         = $80000006;
```

These values are defined in the Windows unit.

The property defaults to `HKEY_CURRENT_USER`.

**Note:** The registry root key can also be specified by handling _[OnGetRegData](TPJRegWdwStateOnGetRegData.md)_ or _[OnGetRegDataEx](TPJRegWdwStateOnGetRegDataEx.md)_**<sup>v5.6</sup>** events. If this is done then the value of _RootKey_ is ignored.

### Alternative Property ###

The _[RootKeyEx](TPJRegWdwStateRootKeyEx.md)_**<sup>v5.6</sup>** property provides an alternative way of setting the registry root key. Instead of taking an _HKEY_ value it takes a value from the _[TPJRegRootKey](TPJRegRootKey.md)_**<sup>v5.6</sup>** enumeration, making it impossible to specify an invalid value.

_[RootKeyEx](TPJRegWdwStateRootKeyEx.md)_**<sup>v5.6</sup>** also makes it easier and safer to set values in Delphi's Object Inspector since the required value is selected from a list.

Setting _RootKey_ changes the value of _[RootKeyEx](TPJRegWdwStateRootKeyEx.md)_**<sup>v5.6</sup>** and vice versa.