#summary Description of the TPJResourceFile.IndexOfEntry method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !IndexOfEntry method =

*Project:* [ResFileUnit Resource File Unit]

*Unit:* _PJResFile_.

*Class:* _[TPJResourceFile TPJResourceFile]_

{{{
function IndexOfEntry(const Entry: TPJResourceEntry): Integer;
}}}

Gets the index number of a resource entry in the resource file's _[TPJResourceFileEntries Entries]_ property.

*_Parameter:_*

  * _Entry_: A reference to resource entry to be found.

*_Returns:_*

The index of the resource entry in the _[TPJResourceFileEntries Entries]_ property or `-1` if not found.
