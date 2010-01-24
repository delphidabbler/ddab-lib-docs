#summary Description of the TPJDropFiles.FileName property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !FileName property =

*Project:* [DropFilesComponents Drop Files Components].

*Unit:* _PJDropFiles_.

*Class:* _[TPJDropFiles TPJDropFiles]_

{{{
property FileName: string;
}}}

== Description ==

The name of a file dropped on the control or its child controls.

When a file is dropped on the control, this read-only property contains the fully specified name of the file. If more than one file is dropped, this property stores the name of the first file dropped. If no files have been dropped then the empty string is returned. 

Note: when one or more files have been dropped _!FileName_ is the same as the first element of the _[TPJDropFilesFiles Files]_ property. If no files are available then _!FileName_ = ''.
