#summary Description of the TPJDropFiles.Count property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Count property =

*Project:* [DropFilesComponents Drop Files Components].

*Unit:* _PJDropFiles_.

*Class:* _[TPJDropFiles TPJDropFiles]_

{{{
property Count: Integer;
}}}

== Description ==

This read only property returns the number of files dropped on the _TPJDropFiles_ control or its child controls.

The names of the dropped files are stored in the _[TPJDropFilesFiles Files]_ array property and are indexed from 0 to _Count_ - 1.

Files filtered out via the _[TPJDropFilesOptions Options]_ and _[TPJDropFilesFilter Filter]_ properties or the _[TPJDropFilesOnFileFilter OnFileFilter]_ event handler are not included in the _Files_ or _Count_ properties.
