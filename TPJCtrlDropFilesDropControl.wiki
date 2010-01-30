#summary Description of the TPJCtrlDropFiles.DropControl property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !DropControl property =

*Project:* [DropFilesComponents Drop Files Components].

*Unit:* _PJDropFiles_.

*Class:* _[TPJCtrlDropFiles TPJCtrlDropFiles]_

{{{
property DropControl: TControl;
}}}

== Description ==

Provides a reference to any control parented by the managed control that was under the mouse cursor when files were dropped. If no child controls were under the cursor then a reference to managed control itself is returned.
