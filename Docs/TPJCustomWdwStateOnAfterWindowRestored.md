# OnAfterWindowRestored event #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJCustomWdwState](TPJCustomWdwState.md)_

**Introduced:** v5.4

```pascal
property OnAfterWindowRestored: TNotifyEvent;
```

## Description ##

This published event is triggered just after the window has been restored. This occurs either after program start-up if the _[AutoSaveRestore](TPJCustomWdwStateAutoSaveRestore.md)_ property is True or after the _[Restore](TPJCustomWdwStateRestore.md)_ method has been called.

Handle this event if you need to determine the state of the restored window or its restored size. Use methods of the host form to find the required information.

See also: _[OnAfterWindowSized](TPJCustomWdwStateOnAfterWindowSized.md)_ **<sup>v5.4</sup>**