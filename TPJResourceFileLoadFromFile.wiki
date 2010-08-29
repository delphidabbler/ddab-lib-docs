#summary Description of the TPJResourceFile.LoadFromFile method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !LoadFromFile method =

*Project:* [ResFileUnit Resource File Unit]

*Unit:* _PJResFile_.

*Class:* _[TPJResourceFile TPJResourceFile]_

{{{
procedure LoadFromFile(const FileName: TFileName);
}}}

Loads a resource file from a named file. New _[TPJResourceEntry TPJResourceEntry]_ objects are created for each resource in the file.

Any _[TPJResourceEntry TPJResourceEntry]_ objects that existed before calling _!LoadFromFile_ are freed. You should be careful not to access any existing references to such objects after calling _!LoadFromFile_.

*_Parameter:_*

  * _!FileName_: The name of the file from which to load the resource data.

*_Raises:_*

Exceptions are raised if the file does not exist or does not contain a valid resource file.
