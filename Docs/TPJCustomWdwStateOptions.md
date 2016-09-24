# Options property #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJCustomWdwState](TPJCustomWdwState.md)_

```pascal
type TPJWdwStateOptions = set of (
  woIgnoreState, woIgnoreSize, woFitWorkArea
);

property Options: TPJWdwStateOptions;
```

## Description ##

The _Options_ property records various display options used when displaying windows after reading display data from storage. The following values can be included in the _Options_ set.

| Value | Description |
|:----------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `woIgnoreState` | Determines the state applied to the window when when restored by the component: minimised, maximised or normal. By default the window is restored to the state read from storage. When this option is specified the stored state is ignored and the window is always displayed in the normal state. Including or excluding this value also sets the deprecated _[IgnoreState](TPJCustomWdwStateIgnoreState.md)_ property to true or false respectively, and vice versa. |
| `woIgnoreSize` | Determines the how the size of the stored window is set. By default the window's size is read from storage. When the option is set the stored size is ignored and the window is displayed using its default size: i.e. the size of the window's form as designed. Setting this option also prevents the `woFitWorkArea` option from resizing the window. |
| `woFitWorkArea` | When this option is set the restored window appears wholy within the appropriate monitor's desktop work area (i.e. the area of the dektop not occupied by the task bar and any other Windows toolbars). This means that if any part of the restored window would appear outside the work area it is re-positioned to be completely contained in the work area. If the window is too wide or high to fit the window the action taken depends on the `woIgnoreSize` option. When used with MDI child forms this option treats the main MDI form's client area as the work area. When `woFitWorkArea` is not set the window is never repositioned within the work area. |

By default the _Options_ property is the empty set.

The _[Save](TPJCustomWdwStateSave.md)_ method always records the window state and size, regardless of whether `woIgnoreState` and `woIgnoreSize` are set. The saved state and/or size is simply ignored when one or both of these option are set.
