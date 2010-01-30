#summary Description of the TPJCtrlDropFiles.OnFileFilter event
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !OnFileFilter event =

*Project:* [DropFilesComponents Drop Files Components].

*Unit:* _PJDropFiles_.

*Class:* _[TPJCtrlDropFiles TPJCtrlDropFiles]_

{{{
property OnFileFilter: TPJDroppedFileFilter;
}}}

== Description ==

This event is triggered for each dropped file and folder handled on behalf of the managed control and has type _[TPJDroppedFileFilter TPJDroppedFileFilter]_. The file or folder can be omitted from the list of dropped files by altering the _Accept_ parameter of the event handler from True to False.

Folders that are filtered out by this event are not added to the _[TPJCtrlDropFilesFiles Files]_ property but are still scanned when the `dfoRecurseFolders` is included in _[TPJCtrlDropFilesOptions Options]_.

Note that the _[TPJCtrlDropFilesFilter Filter]_ property takes precedence and files filtered out by the associated filter component are not processed by this event.
