# AutoSaveRestore property #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJCustomWdwState](TPJCustomWdwState.md)_

```pascal
property AutoSaveRestore: Boolean;
```

## Description ##

Determines whether the window's size, position and state is automatically restored on creation and stored on destruction.

The _AutoSaveRestore_ property, when set to true, causes the component to automatically restore the owning containing form's size, position and state when the window is created and to save the information when the window is destroyed.

The property should set at design time. Setting the property at run time has no effect on whether the window's state is restored, since the window will already be created. However, changing the property at run time does determine whether the window's display attributes are saved automatically on exit.

The effect of the property is equivalent to placing a call to _Restore_ in the form's _OnCreate_ or _OnShow_ event handlers and to a call to _Save_ in the form's _OnDestroy_ event handler.

The default value of this property is False.