#summary Description of the TPJExtFileFilter.Style property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Style property =

*Project:* [DropFilesComponents Drop Files Components].

*Unit:* _PJDropFiles_.

*Class:* _[TPJExtFileFilter TPJExtFileFilter]_

{{{
property Style: TPJExtFileFilterStyle;
}}}

== Description ==

This property determines which kinds of file names have the extension filter applied. Possible values are given by the _[TPJExtFileFilterStyleEnum TPJExtFileFilterStyle]_ enumeration.

The default value is `fsFilterFilesOnly`.

Note: To prevent files or folders passing through the filter being accepted by the drop files control, set the control's _Options_ property appropriately.
