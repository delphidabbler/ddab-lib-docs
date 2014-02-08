#summary Message Dialogue Components documentation.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Message Dialogue Components =

The Message Dialogue Components are supplied in a single unit named _PJMessageDialog_. There are two components:

|| *Class* || *Description* ||
|| _[TPJWinMsgDlg TPJWinMsgDlg]_ || This component wraps the Windows _!MessageBoxIndirect_ API call and displays a message box based on that provided by Windows. This component will be suitable for most purposes and has the lighter footprint. ||
|| _[TPJVCLMsgDlg TPJVCLMsgDlg]_  || This component uses the Delphi VCL _!CreateMessageDialog_  function to create a form based message box. The component provides more flexibility than either the Delphi functions or _[TPJWinMsgDlg TPJWinMsgDlg]_. It should be used when it is necessary to display buttons or combinations of buttons that are not supported by the Windows API message box or when a finer degree of control over the appearance and behaviour of the message box is required. _TPJVCLMsgDlg_ supports all the features of _[TPJWinMsgDlg TPJWinMsgDlg]_ and extends them. The dialogue box component's form can been customised by handling the _[TPJVCLMsgDlgOnShow OnShow]_ and _[TPJVCLMsgDlgOnHide OnHide]_ events. ||

*Note:* This documentation applies to release 3.0.0 and later. Earlier versions had an additional component named _TPJMessageDialog_ that was deprecated in later v2 releases and removed at v3.


*Links:*

  * Back to [Welcome Wiki Home Page]
  * [http://www.delphidabbler.com/software/msgdlg Message Dialogue Components Web Page].