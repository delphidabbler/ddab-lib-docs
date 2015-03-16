#summary Description of the TPJFormDropFiles.OnDropFiles event
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !OnDropFiles event =

*Project:* [DropFilesComponents Drop Files Components].

*Unit:* _PJDropFiles_.

*Class:* _[TPJFormDropFiles TPJFormDropFiles]_

{{{
property OnDropFiles: TNotifyEvent;
}}}

== Description ==

This event is triggered after files have been dropped on the form and the files have been processed. When this event is triggered all the dropped files are available in the _[TPJFormDropFilesFiles Files]_  property.

This event is not triggered when the _[TPJFormDropFilesEnabled Enabled]_ property is False.
