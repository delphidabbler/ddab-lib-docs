#summary Description of the TPJDropFiles.IsFolder property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !IsFolder property =

*Project:* [DropFilesComponents Drop Files Components].

*Unit:* _PJDropFiles_.

*Class:* _[TPJDropFiles TPJDropFiles]_

{{{
property IsFolder[Idx: Integer]: Boolean;
}}}

== Description ==

This read-only array property informs whether the file at the same index in the _[TPJDropFilesFiles Files]_ property is a folder (true) or a file (false). The array is zero based and is indexed from 0.._[TPJDropFilesCount Count]_-1. Attempts to access array elements outside this range result in an exception being raised.
