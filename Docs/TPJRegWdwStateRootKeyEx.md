# RootKeyEx property #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJRegWdwState](TPJRegWdwState.md)_

**Introduced:** v5.6

```pascal
property RootKeyEx: TPJRegRootKey;
```

## Description ##

This property allows the user to specify the registry root key under which the window size, position and state information is recorded. The information is saved in a subkey of this root key determined by the _[SubKey](TPJRegWdwStateSubKey.md)_ property.

_RootKeyEx_ can take any of the values of the _[TPJRegRootKey](TPJRegRootKey.md)_**<sup>v5.6</sup>** enumeration.

The property defaults to `hkCurrentUser`.

**Note:** The registry root key can also be specified by handling _[OnGetRegDataEx](TPJRegWdwStateOnGetRegDataEx.md)_**<sup>v5.6</sup>** or _[OnGetRegData](TPJRegWdwStateOnGetRegData.md)_ events. If this is done then the value of _RootKeyEx_ is ignored.

### Alternative Property ###

The _[RootKey](TPJRegWdwStateRootKey.md)_ property provides an alternative way of setting the registry root key. Instead of taking a _[TPJRegRootKey](TPJRegRootKey.md)_**<sup>v5.6</sup>** value it takes an _HKEY_. **Note:** This property has been retained for backwards compatibilty reasons. You are recommended to use _RootKeyEx_ in all new code.

There are two main reason why _RootKeyEx_ is considered superior to _[RootKey](TPJRegWdwStateRootKey.md)_:

  1. It is impossible to specify an invalid root key value when using _RootKeyEx_ because its value is restricted to those of the _[TPJRegRootKey](TPJRegRootKey.md)_**<sup>v5.6</sup>** enumeration which are all valid. Conversely it is easy to provide an invalid _HKEY_ value to _[RootKey](TPJRegWdwStateRootKey.md)_.
  1. _RootKeyEx_ displays its values in a user-friendly way in Delphi's Object Inspector: the user chooses a value from a drop-down list of values. With _[RootKey](TPJRegWdwStateRootKey.md)_ the user has to type the correct HKEY value into the Object Inspector.

Setting _RootKeyEx_ changes the value of _[RootKey](TPJRegWdwStateRootKey.md)_ and vice versa.