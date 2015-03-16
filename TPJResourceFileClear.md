#summary Description of the TPJResourceFile.Clear method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Clear method =

*Project:* [ResFileUnit Resource File Unit]

*Unit:* _PJResFile_.

*Class:* _[TPJResourceFile TPJResourceFile]_

{{{
procedure Clear;
}}}

Clears all resources from the resource file object, making the resource file empty. Calling _Clear_ on an already empty resource file object does nothing.

All the _[TPJResourceEntry TPJResourceEntry]_ objects representing the resources are freed. You should make sure that you don't keep or use any references to such objects after calling _Clear_.