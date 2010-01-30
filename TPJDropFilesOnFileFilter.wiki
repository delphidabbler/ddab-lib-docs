#summary Description of the TPJDropFiles.OnFileFilter event
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !OnFileFilter event =

*Project:* [DropFilesComponents Drop Files Components].

*Unit:* _PJDropFiles_.

*Class:* _[TPJDropFiles TPJDropFiles]_

{{{
property OnFileFilter: TPJDroppedFileFilter;
}}}

== Description ==

This event is triggered for each dropped file and folder handled by the control and has type _[TPJDroppedFileFilter TPJDroppedFileFilter]_. The file or folder can be omitted from the list of dropped files by altering the _Accept_ parameter of the event handler from True to False.

Folders that are filtered out by this event are not added to the _[TPJDropFilesFiles Files]_ property but are still scanned when the `dfoRecurseFolders` is included in _[TPJDropFilesOptions Options]_.

Note that the _[TPJDropFilesFilter Filter]_ property takes precedence and files filtered out by the associated filter component are not processed by this event.
