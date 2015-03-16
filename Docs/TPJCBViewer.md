<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# TPJCBViewer #

**Project:** [Clipboard Viewer Component](ClipboardViewerComponent.md).

**Unit:** _PJCBView_.

_TPJCBViewer_ notifies the user of changes to the Windows clipboard. It registers itself with Windows to receive notifications whenever the contents of the clipboard change. When a change is detected the _[OnClipboardChanged](TPJCBViewerOnClipboardChanged.md)_ event is triggered. Users handle this event.

The component also provides an _[Enabled](TPJCBViewerEnabled.md)_ property which, when `False`, prevents _[OnClipboardChanged](TPJCBViewerOnClipboardChanged.md)_ events from being triggered. It also has a _[TriggerOnCreation](TPJCBViewerTriggerOnCreation.md)_ property which, when `True`, causes the _[OnClipboardChanged](TPJCBViewerOnClipboardChanged.md)_ event to be triggered immediately after the control has been created as well as when the clipboard contents change.

## Methods ##

_TPJCBViewer_ defines no new methods.

## Properties ##

| **Property** | **Description** |
|:-------------|:----------------|
| _[Enabled](TPJCBViewerEnabled.md)_ | Enables and disables the component. |
| _Name_ | Inherited from _TComponent_. See Delphi help for details. |
| _Tag_ | Inherited from _TComponent_. See Delphi help for details. |
| _[TriggerOnCreation](TPJCBViewerTriggerOnCreation.md)_ | Causes a clipboard change event to be triggered when the component is created. |

## Events ##

| **Event** | **Description** |
|:----------|:----------------|
| _[OnClipboardChanged](TPJCBViewerOnClipboardChanged.md)_ | Event triggered when the clipboard contents change. |