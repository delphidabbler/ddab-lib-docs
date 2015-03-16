#summary Description of the TPJResourceFile.Entries property.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Entries property =

*Project:* [ResFileUnit Resource File Unit]

*Unit:* _PJResFile_.

*Class:* _[TPJResourceFile TPJResourceFile]_

{{{
property Entries[Idx: Integer]: TPJResourceEntry;
}}}

This read-only property provides indexed access to all the resources in the resource file. Valid indices are in the range 0 to _[TPJResourceFileEntryCount EntryCount]_ - 1.
