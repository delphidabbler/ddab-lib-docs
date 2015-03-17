# OnAfterWindowSized event #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJCustomWdwState](TPJCustomWdwState.md)_

**Introduced:** v5.4

```pascal
property OnAfterWindowSized: TNotifyEvent;
```

## Description ##

This published event is triggered just after the window's size has been set. This occurs before the window is actually restored on screen and before its state has been set.

Handle this event if you need to determine the _normal_ size and position of the window, regardless of its final state. Use methods of the host form to find the required size and position information.

See also: _[OnAfterWindowRestored](TPJCustomWdwStateOnAfterWindowRestored.md)_ **<sup>v5.4</sup>**