# Execute method #

**Project:** [Message Dialogue Components](MessageDialogComponents.md).

**Unit:** _PJMessageDialog_.

**Class:** _[TPJVCLMsgDlg](TPJVCLMsgDlg.md)_

```pascal
function Execute: Integer;
```

## Description ##

Call _Execute_ to display the dialogue box. _Execute_ returns a value associated with the button that was clicked to close the dialogue box.

Use the _[ButtonGroup](TPJVCLMsgDlgButtonGroup.md)_ or _[Buttons](TPJVCLMsgDlgButtons.md)_ properties to determine which buttons are displayed in the dialogue box. The return values are defined in the _Controls_ unit. The return values for buttons that are common both to _Windows_ and the Delphi _Controls_ unit are the same - i.e. the Delphi constants representing theses values map onto those defined by Windows. The possible return values of the various buttons are:

| **Button clicked** | **Return value** | **Windows Equivalent** |
|:-------------------|:-----------------|:-----------------------|
| Yes | `mrYes` | `IDYES` |
| No | `mrNo` | `IDNO` |
| OK | `mrOK` | `IDOK` |
| Cancel | `mrCancel` | `IDCANCEL` |
| Abort | `mrAbort` | `IDABORT` |
| Retry | `mrRetry` | `IDRETRY` |
| Ignore | `mrIgnore` | `IDIGNORE` |
| All | `mrAll` | N/a |
| No To All | `mrNoToAll` | N/a |
| Yes To All | `mrYesToAll` | N/a |
| Help | N/a (doesn't close dialogue) | N/a |
| Close | `mrClose` (later Delphis only) | N/a |
