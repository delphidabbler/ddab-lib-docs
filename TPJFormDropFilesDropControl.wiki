#summary Description of the TPJFormDropFiles.DropControl property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !DropControl property =

*Project:* [DropFilesComponents Drop Files Components].

*Unit:* _PJDropFiles_.

*Class:* _[TPJFormDropFiles TPJFormDropFiles]_

{{{
property DropControl: TControl;
}}}

== Description ==

Provides a reference to any control on the form that was under the mouse when the files were dropped. If no controls were under the cursor then a reference to the form is returned providing the mouse was in the form's client area. Nil is returned otherwise.
