#summary Description of the TPJCtrlDropFiles.Enabled property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Enabled property =

*Project:* [DropFilesComponents Drop Files Components].

*Unit:* _PJDropFiles_.

*Class:* _[TPJCtrlDropFiles TPJCtrlDropFiles]_

{{{
property Enabled: Boolean;
}}}

== Description ==

_Enabled_ determines whether dropped files are handled or ignored. When _Enabled_ is true the component handles all file drop messages to the managed control. When false, file drops are ignored and are passed through to the owning form.
