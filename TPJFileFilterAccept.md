#summary Description of the TPJFileFilter.Accept method
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Accept method =

*Project:* [DropFilesComponents Drop Files Components].

*Unit:* _PJDropFiles_.

*Class:* _[TPJFileFilter TPJFileFilter]_

{{{
function Accept(
  const FilePath: string; const IsFolder: Boolean
): Boolean; virtual; abstract;
}}}

== Description ==

Checks whether a given file or folder passes though a filter.

This abstract method is called by the filter's owning drop files component whenever files are dropped. It is called once for each file or folder dropped. Its purpose is to determine which of the dropped files or folders are to pass through the filter. _!FilePath_ is the fully qualified path of the file or folder concerned, while _!IsFolder_ indicates whether _!FilePath_ is a file or folder. The method returns true to indicate a file or folder passes through the filter and false if it is to be filtered out.

Files and folders that do not pass the filter are not passed to the drop files component's _!OnFileFilter_ event handler and are not added to the component's _Files_ array property.

Note: This method is abstract and must be implemented in an appropriate way by decendant classes.
