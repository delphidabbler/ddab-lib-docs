#summary Description of the TPJDropFiles.Enabled property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Enabled property =

*Project:* [DropFilesComponents Drop Files Components].

*Unit:* _PJDropFiles_.

*Class:* _[TPJDropFiles TPJDropFiles]_

{{{
property Enabled: Boolean;
}}}

== Description ==

_Enabled_ determines whether dropped files are handled or ignored. When _Enabled_ is true the control handles all file drop messages sent to itself. When false file drops are ignored and messages are passed to the owning form.
