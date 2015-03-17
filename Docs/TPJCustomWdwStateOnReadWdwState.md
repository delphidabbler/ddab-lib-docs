# OnReadWdwState event #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJCustomWdwState](TPJCustomWdwState.md)_

```pascal
type
  TPJWdwStateReadEvent = procedure(
    Sender: TObject; var Left, Top, Width, Height, State: Integer
  ) of object;

property OnReadWdwState: TPJWdwStateReadEvent;
```

## Description ##

This event is triggered just after the window placement, size and state data is read from storage but before displaying the window. The data can be modified in the event handler before the window is displayed, enabling the size, placement and state of the window to be changed.

Setting any of the parameters to _MaxInt_ causes the default value for the parameter to be used. These default values come from the relevant properties of the related form.

If _[Options](TPJCustomWdwStateOptions.md)_ property contains the `woIgnoreState` value then any changes to the _State_ parameter in the event handler are ignored. Similarly if _[Options](TPJCustomWdwStateOptions.md)_ contains `woIgnoreSize` then changes to _Width_ and _Height_ are ignored and default values are used. Finally, if _[Options](TPJCustomWdwStateOptions.md)_ contains `woFitWorkArea` then the _Top_, _Left_, and (if `woIgnoreSize` is not specified) _Width_ and _Height_ values may be altered to ensure the window fits in the workspace.

The event is protected in _[TPJCustomWdwState](TPJCustomWdwState.md)_. It may be exposed by derived components.