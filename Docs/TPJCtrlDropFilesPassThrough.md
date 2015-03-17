# PassThrough property #

**Project:** [Drop Files Components](DropFilesComponents.md).

**Unit:** _PJDropFiles_.

**Class:** _[TPJCtrlDropFiles](TPJCtrlDropFiles.md)_

```pascal
property PassThrough: Boolean;
```

## Description ##

_PassThrough_ causes drop files messages to be optionally passed through to the owning form.

When the property is false (default), and the control is enabled, any drop files messages intercepted by this control on behalf of the managed control are not forwarded to the form.

When _PassThrough_ is true, and the control is enabled, then normal processing occurs when files are dropped. `WM_DROPFILES` messages are converted to custom `PJ_DROPFILES` message and forwarded to the form. Any _[TPJFormDropFiles](TPJFormDropFiles.md)_ component on the form can intercept `PJ_DROPFILES` messages and handle them like a standard `WM_DROPFILES` message.

When the drop files message is passed through, the drop point is converted into form coordinates and sent to the form as part of the `PJ_DROPFILES` message. In this way a _[TPJFormDropFiles](TPJFormDropFiles.md)_ component has its _[DropPoint](TPJFormDropFilesDropPoint.md)_ property set to the correct value in terms of the form.