#summary Description of the TPJCtrlDropFiles.OnDropFiles event
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !OnDropFiles event =

*Project:* [DropFilesComponents Drop Files Components].

*Unit:* _PJDropFiles_.

*Class:* _[TPJCtrlDropFiles TPJCtrlDropFiles]_

{{{
property OnDropFiles: TNotifyEvent;
}}}

== Description ==

This event is triggered after files have been dropped on the managed control and the files have been processed. When this event is triggered all the dropped files are available in the _[TPJCtrlDropFilesFiles Files]_  property.

This event is not triggered when the _[TPJCtrlDropFilesEnabled Enabled]_ property is False.
