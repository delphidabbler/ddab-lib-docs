<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# Enabled property #

**Project:** [Clipboard Viewer Component](ClipboardViewerComponent.md).

**Unit:** _PJCBView_.

**Class:** _[TPJCBViewer](TPJCBViewer.md)_

```
property Enabled: Boolean;
```

## Description ##

The _Enabled_ property enables and disables the component.

When the property is set to `False` the component will never trigger the _[OnClipboardChanged](TPJCBViewerOnClipboardChanged.md)_ event. Restoring _Enabled_ to `True` re-enables _[OnClipboardChanged](TPJCBViewerOnClipboardChanged.md)_.

The default value is `True`.