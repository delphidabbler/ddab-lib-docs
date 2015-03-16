#summary Description of the TPJFormDropFiles.Count property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Count property =

*Project:* [DropFilesComponents Drop Files Components].

*Unit:* _PJDropFiles_.

*Class:* _[TPJFormDropFiles TPJFormDropFiles]_

{{{
property Count: Integer;
}}}

== Description ==

This read only property returns the number of files dropped on the form.

The names of the dropped files are stored in the _[TPJFormDropFilesFiles Files]_ array property and are indexed from 0 to _Count_ - 1.

Files filtered out via the _[TPJFormDropFilesOptions Options]_ and _[TPJFormDropFilesFilter Filter]_ properties or the _[TPJFormDropFilesOnFileFilter OnFileFilter]_ event handler are not included in the _Files_ or _Count_ properties.
