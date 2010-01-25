#summary Description of the TPJCtrlDropFiles.Count property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Count property =

*Project:* [DropFilesComponents Drop Files Components].

*Unit:* _PJDropFiles_.

*Class:* _[TPJCtrlDropFiles TPJCtrlDropFiles]_

{{{
property Count: Integer;
}}}

== Description ==

This read only property returns the number of files dropped on the managed control.

The names of the dropped files are stored in the _[TPJCtrlDropFilesFiles Files]_ array property and are indexed from 0 to _Count_ - 1.

Files filtered out via the _[TPJCtrlDropFilesOptions Options]_ and _[TPJCtrlDropFilesFilter Filter]_ properties or the _[TPJCtrlDropFilesOnFileFilter OnFileFilter]_ event handler are not included in the _Files_ or _Count_ properties.
