#summary Description of the TPJExtFileFilterStyle enumeration.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= TPJExtFileFilterStyle enumeration =

*Project:* [DropFilesComponents Drop Files Components].

*Unit:* _PJDropFiles_.

{{{
type
  TPJExtFileFilterStyle = (
    fsFilterFilesOnly, fsFilterFoldersOnly, fsAll
  );
}}}

== Description ===

This enumeration represents the kind of filtering performed by the _[TPJExtFileFilter TPJExtFileFilter]_ component according to its _[TPJExtFileFilterStyle Style]_ property. Possible values are:

|| `fsFilterFilesOnly` || Files are filtered by their extension while all folders are passed through the filter regardless of extension. ||
|| `fsFilterFoldersOnly` || Folders are filtered by their extension while all files are passed through the filter. ||
|| `fsAll` || The filter is applied to both files and folders. ||
