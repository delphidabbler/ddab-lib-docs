# Execute method #

**Project:** [Message Dialogue Components](MessageDialogComponents.md).

**Unit:** _PJMessageDialog_.

**Class:** _[TPJWinMsgDlg](TPJWinMsgDlg.md)_

```pascal
function Execute: Integer;
```

## Description ##

Call _Execute_ to display the dialogue box. _Execute_ returns a value associated with the button that was clicked to close the dialogue box as follows:

| **Button clicked** | **Return value** |
|:-------------------|:-----------------|
| Abort | `IDABORT` (3) |
| Cancel | `IDCANCEL` (2) |
| Continue | `IDCONTINUE` (11) |
| Ignore | `IDIGNORE` (5) |
| No | `IDNO` (7) |
| OK | `IDOK` (1) |
| Retry | `IDRETRY` (4) |
| Try Again | `IDTRYAGAIN` (10) |
| Yes | `IDYES` (6) |