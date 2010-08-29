#summary Description of the TPJResourceFile.SaveToFile method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !SaveToFile method =

*Project:* [ResFileUnit Resource File Unit]

*Unit:* _PJResFile_.

*Class:* _[TPJResourceFile TPJResourceFile]_

{{{
procedure SaveToFile(const FileName: TFileName);
}}}

Creates a 32 bit resource file containing all the resources recorded in the resource file object. If there are no resource entries then a valid empty resource file is created.

*_Parameter:_*

  * _!FileName_: The name of the resource file to be created.

*_Raises:_*

An exception is raised if the file cannot be created.
