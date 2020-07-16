# TPJCBViewer class

**Project:** [Clipboard Viewer Component](../../CBView.md)

**Unit:** _PJCBView_

_TPJCBViewer_ notifies the user of changes to the Windows clipboard. It registers itself with Windows to receive notifications whenever the contents of the clipboard change. When a change is detected the [_OnClipboardChanged_](./TPJCBViewer-OnClipboardChanged.md) event is triggered. Users handle this event.

The component also provides an [_Enabled_](./TPJCBViewer-Enabled.md) property which, when _False_, prevents [_OnClipboardChanged_](./TPJCBViewer-OnClipboardChanged.md) events from being triggered. It also has a [_TriggerOnCreation_](./TPJCBViewer-TriggerOnCreation.md) property which, when _True_, causes the [_OnClipboardChanged_](./TPJCBViewer-OnClipboardChanged.md) event to be triggered immediately after the control has been created as well as when the clipboard contents change.

## Methods

_TPJCBViewer_ defines no new methods.

## Properties

| Property | Description |
|----------|-------------|
| [_Enabled_](./TPJCBViewer-Enabled.md) | Enables and disables the component. |
| _Name_ | Inherited from _TComponent_. See Delphi help for details. |
| _Tag_ | Inherited from _TComponent_. See Delphi help for details. |
| [_TriggerOnCreation_](./TPJCBViewer-TriggerOnCreation.md) | Causes a clipboard change event to be triggered when the component is created. |

## Events

| Event | Description |
|-------|-------------|
| [_OnClipboardChanged_](./TPJCBViewer-OnClipboardChanged.md) | Event triggered when the clipboard contents change. |
