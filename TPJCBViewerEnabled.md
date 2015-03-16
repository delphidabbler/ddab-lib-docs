#summary Description of the TPJCBViewer.Enabled property.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Enabled property =

*Project:* [ClipboardViewerComponent Clipboard Viewer Component].

*Unit:* _PJCBView_.

*Class:* _[TPJCBViewer TPJCBViewer]_

{{{
property Enabled: Boolean;
}}}

== Description ==

The _Enabled_ property enables and disables the component.

When the property is set to `False` the component will never trigger the _[TPJCBViewerOnClipboardChanged OnClipboardChanged]_ event. Restoring _Enabled_ to `True` re-enables _[TPJCBViewerOnClipboardChanged OnClipboardChanged]_.

The default value is `True`.