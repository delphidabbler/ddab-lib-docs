# TriggerOnCreation property

**Project:** [Clipboard Viewer Component](../../CBView.md)

**Unit:** _PJCBView_

**Class:** [_TPJCBViewer_](./TPJCBViewer.md)

```pascal
property TriggerOnCreation: Boolean;
```

## Description

This property controls whether a clipboard change event is triggered when the component is created.

When _TriggerOnCreation_ is _True_ the [_OnClipboardChanged_](./TPJCBViewer-OnClipboardChanged.md) event is triggered immediately after the component is created, regardless of whether the clipboard has changed. This behaviour is useful because you often need to check the clipboard content at program start up as well as when the content changes. By using this feature you simply need to code the event handler and don't need any special start up code.

When the property is _False_ the [_OnClipboardChanged_](./TPJCBViewer-OnClipboardChanged.md) event is only triggered when the content of the clipboard actually changes.

## Notes

* This is a design-time only property. Setting it dynamically at run time will have no effect since the component will have been initialised before the user gets a chance to change the property's value.
* This property has no effect if [_Enabled_](./TPJCBViewer-Enabled.md) is set to _False_ at design time. In this case no event is fired after component creation, even if _TriggerOnCreation_ is _True_.

The default value is _True_.
