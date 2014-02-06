#summary Description of the TPJVCLMsgDlg.IconResource property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !IconResource property =

*Project:* [MessageDialogComponents Message Dialogue Components].

*Unit:* _PJMessageDialog_.

*Class:* _[TPJVCLMsgDlg TPJVCLMsgDlg]_

{{{
property IconResource: string;
}}}

== Description ==

Set _!IconResource_ to identify the resource to be used to display a user defined icon in the dialogue box. If _!IconResource_ is left blank then the default resource name "MAINICON" is used. The icon resource must be contained in the executable file. If such a resource cannot be found then no icon is displayed.

The _[TPJVCLMsgDlgKind Kind]_ property must be set to `mkUser` and `mdoShowCustomIcon` must be included in the set of _[TPJVCLMsgDlgOptions Options]_ in order to display a user defined icon. _!IconResource_ is ignored if _[TPJVCLMsgDlgKind Kind]_ has any other value or if the required option is not set.

*Note 1:* "MAINICON" is the resource name of the application's main icon in Delphi.

*Note 2:* To reference an icon resource with a numeric id (rather than a string name) preceed the numeric value by a '#' character.
