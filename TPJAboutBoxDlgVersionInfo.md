#summary Description of the TPJAboutBoxDlg.VersionInfo property.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !VersionInfo property =

*Project:* [AboutBoxComponent About Box Component].

*Unit:* _PJAbout_. 

*Class:* _[TPJAboutBoxDlg TPJAboutBoxDlg]_

{{{
property VersionInfo: TPJVersionInfo;
}}}

== Description ==

This property allows information from a string information block in a program file's _VERSIONINFO_ resource to be displayed in the dialog box.

To enable this to happen a _[TPJVersionInfo TPJVersionInfo]_ component must be placed on the form and this property must reference it. The _TPJVersionInfo_ component's _[TPJVersionInfoFileName FileName]_ property must be set to the name of the executable file from which version information is to be extracted, or set to '' to get the version information of the parent executable file. 

The following table shows which version information string values are used, along with the properties whose values they replace:

|| *VERSIONINFO string* || Replaces property ||
|| !ProductName || _[TPJAboutBoxDlgProgramName ProgramName]_ ||
|| !ProductVersion || _[TPJAboutBoxDlgVersion Version]_ ||
|| !LegalCopyright || _[TPJAboutBoxDlgCopyright Copyright]_ ||
|| Comments || _[TPJAboutBoxDlgNotes Notes]_ ||

If any of these string values are not present in the version information nothing is displayed in their place. 

If the _!VersionInfo_ property is set to nil then the information displayed in the dialog box is taken from the string properties listed in the table above.

This property has no effect on the _[TPJAboutBoxDlgTitle Title]_ property.
