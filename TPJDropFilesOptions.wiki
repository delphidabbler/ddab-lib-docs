#summary Description of the TPJDropFiles.Options property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Options property =

*Project:* [DropFilesComponents Drop Files Components].

*Unit:* _PJDropFiles_.

*Class:* _[TPJDropFiles TPJDropFiles]_

{{{
property Options: TPJDropFilesOptions;
}}}

== Description ==

This property determines how dropped files are interpreted. The resulting files are made available through the _[TPJDropFilesFiles Files]_ property. The property can take any one or more of the values from the _[TPJDropFilesOptionsSet TPJDropFilesOptions]_ set.

It makes no sense to omit both the `dfoIncFiles` and `dfoIncFolders` options since no files will pass the filter.
