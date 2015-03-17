# Cursor property #

**Project:** [Hot Label Component](HotLabelComponent.md).

**Unit:** _PJHotLabel_.

**Class:** _[TPJHotLabel](TPJHotLabel.md)_

```pascal
property Cursor: TCursor;
```

## Description ##

_Cursor_ specifies the image used to represent the mouse pointer when it passes into the region covered by the control.

Change the value of _Cursor_ to provide feedback to the user about what action is appropriate when the mouse pointer enters the control.

The value of _Cursor_ is the index of the cursor in the list of cursors maintained by the global variable, _Screen_. In addition to the built-in cursors provided by _TScreen_, applications can add custom cursors to the list. See the inherited _Cursor_ property of _TControl_ for further details.

The _Cursor_ property of _[TPJHotLabel](TPJHotLabel.md)_ differs from the inherited property in that its default cursor is `crHandPoint` rather than `crDefault`.

**Note:** Earlier versions of the component used a custom cursor named `crHand`. For backward compatibility this constant is defined in the _PJHotLabel_ unit to have the same value as `crHandPoint`.