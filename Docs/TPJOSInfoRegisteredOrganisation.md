# RegisteredOrganisation class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJOSInfo](TPJOSInfo.md)_

**Introduced:** v4.0

```pascal
class function RegisteredOrganisation: string;
```

## Description ##

Returns the organisation to which Windows is registered.

The empty string is returned if no organisation has been reqistered.

**Note the UK English spelling of "Organisation" in this method name.**

**See also**

  * _[RegisteredOwner](TPJOSInfoRegisteredOwner.md)_