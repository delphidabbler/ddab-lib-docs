#summary Description of the TPJCtrlDropFiles.PassThrough property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !PassThrough property =

*Project:* [DropFilesComponents Drop Files Components].

*Unit:* _PJDropFiles_.

*Class:* _[TPJCtrlDropFiles TPJCtrlDropFiles]_

{{{
property PassThrough: Boolean;
}}}

== Description ==

_!PassThrough_ causes drop files messages to be optionally passed through to the owning form.

When the property is false (default), and the control is enabled, any drop files messages intercepted by this control on behalf of the managed control are not forwarded to the form.

When _!PassThrough_ is true, and the control is enabled, then normal processing occurs when files are dropped. `WM_DROPFILES` messages are converted to custom `PJ_DROPFILES` message and forwarded to the form. Any _[TPJFormDropFiles TPJFormDropFiles]_ component on the form can intercept `PJ_DROPFILES` messages and handle them like a standard `WM_DROPFILES` message.

When the drop files message is passed through, the drop point is converted into form coordinates and sent to the form as part of the `PJ_DROPFILES` message. In this way a _[TPJFormDropFiles]_ component has its _[TPJFormDropFilesDropPoint DropPoint]_ property set to the correct value in terms of the form.
