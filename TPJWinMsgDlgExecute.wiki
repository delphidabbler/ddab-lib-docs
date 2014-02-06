#summary Description of the TPJWinMsgDlg.Execute method
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Execute method =

*Project:* [MessageDialogComponents Message Dialogue Components].

*Unit:* _PJMessageDialog_.

*Class:* _[TPJWinMsgDlg TPJWinMsgDlg]_

{{{
function Execute: Integer;
}}}

== Description ==

Call _Execute_ to display the dialogue box. _Execute_ returns a value associated with the button that was clicked to close the dialogue box as follows:

|| *Button clicked* || *Return value* ||
|| Abort || `IDABORT` (3) ||
|| Cancel || `IDCANCEL` (2) ||
|| Continue || `IDCONTINUE` (11) ||
|| Ignore || `IDIGNORE` (5) ||
|| No || `IDNO` (7) ||
|| OK || `IDOK` (1) ||
|| Retry || `IDRETRY` (4) ||
|| Try Again || `IDTRYAGAIN` (10) ||
|| Yes || `IDYES` (6) ||