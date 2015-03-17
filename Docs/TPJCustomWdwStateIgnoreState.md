# IgnoreState property #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJCustomWdwState](TPJCustomWdwState.md)_

```pascal
property IgnoreState: Boolean;
```

## Description ##

**PROPERTY DEPRECATED**

Determines whether the window's saved state (maximised, normal or minimised) is applied on restoration.

Setting _IgnoreState_ to true is the same as including `woIngoreState` in the _[Options](TPJCustomWdwStateOptions.md)_ property, and setting _IgnoreState_ false is the same as excluding `woIngoreState` from _[Options](TPJCustomWdwStateOptions.md)_.

_IgnoreState_ is provided for backwards compatibility purposes only and may be removed from future releases.