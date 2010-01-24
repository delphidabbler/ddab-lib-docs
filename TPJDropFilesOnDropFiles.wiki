#summary Description of the TPJDropFiles.OnDropFiles event
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !OnDropFiles event =

*Project:* [DropFilesComponents Drop Files Components].

*Unit:* _PJDropFiles_.

*Class:* _[TPJDropFiles TPJDropFiles]_

{{{
property OnDropFiles: TNotifyEvent;
}}}

== Description ==

This event is triggered after files have been dropped on the component and the files have been processed. When this event is triggered all the dropped files are available in the _[TPJDropFilesFiles Files]_  property.

This event is not triggered when the _[TPJDropFilesEnabled Enabled]_ property is False.
