#summary Description of the TPJFormDropFiles.Options property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Options property =

*Project:* [DropFilesComponents Drop Files Components].

*Unit:* _PJDropFiles_.

*Class:* _[TPJFormDropFiles TPJFormDropFiles]_

{{{
property Options: TPJDropFilesOptions;
}}}

== Description ==

This property determines how dropped files are interpreted. The resulting files are made available through the _[TPJFormDropFilesFiles Files]_ property. The property can take any one or more of the values from the _[TPJDropFilesOptionsSet TPJDropFilesOptions]_ set.

It makes no sense to omit both the `dfoIncFiles` and `dfoIncFolders` options since no files will pass the filter.
