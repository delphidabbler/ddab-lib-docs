#summary Description of the TPJResourceFile.LoadFromStream method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !LoadFromStream method =

*Project:* [ResFileUnit Resource File Unit]

*Unit:* _PJResFile_.

*Class:* _[TPJResourceFile TPJResourceFile]_

{{{
procedure LoadFromStream(const Stm: TStream);
}}}

Loads a resource file from a stream. The data is read from the current location in the stream. Loading the data updates the stream position. New _[TPJResourceEntry TPJResourceEntry]_ objects are created for each resource in the data stream.

Any _[TPJResourceEntry TPJResourceEntry]_ objects that existed before calling _!LoadFromStream_ are freed. You should be careful not to access any existing references to such objects after calling _!LoadFromStream_.

*_Parameter:_*

  * _Stm_: The stream from which the resource file data is loaded.

*_Raises:_*

An exception is raised if the stream does not contain valid resource file data.
