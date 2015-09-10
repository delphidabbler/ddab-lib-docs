# Product class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJOSInfo](TPJOSInfo.md)_

```pascal
class function Product: TPJOSProduct;

type TPJOSProduct = (
  osUnknownWinNT, osWinNT, osWin2K, osWinXP,
  osUnknownWin9x, osWin95, osWin98, osWinMe,
  osUnknownWin32s, osWinSvr2003, osUnknown, osWinVista,
  osWinSvr2003R2, osWinSvr2008, osWinLater,
  osWin7, osWinSvr2008R2,       // defined in v3.1 and later
  osWin8, osWinSvr2012,         // defined in v3.4 and later
  osWin8Point1, osWinSvr2012R2  // defined in v5.0 and later
);
```

## Description ##

Returns a value from the _TPJOSProduct_ enumeration that identifies the operating system product. Possible values of _TPJOSProduct_ are:

| Code | Description |
|:-----|:------------|
| `osWin95` | Windows 95 or Windows 95 OSR1. |
| `osWin98` | Windows 98 or Windows 98 SE. |
| `osWinMe` | Windows Me. |
| `osWinNT` | Windows NT (v3.51 to v4) - needs major and minor version information to fully identify the version. |
| `osWin2k` | Windows 2000. |
| `osWinXP` | Windows XP. |
| `osWinVista` | Windows Vista. |
| `osWin7` [v3.1] | Windows 7. |
| `osWin8` [v3.4]| Windows 8. |
| `osWin8Point1` [v5.0] | Windows 8.1 - will only be returned if the host application is "manifested" as a Windows 8.1 application, otherwise `osWin8` will be returned for both Windows 8 and Windows 8.1. |
| `osWinSvr2003` | Windows Server 2003. |
| `osWinSvr2003R2` | Windows Server 2003 R 2. |
| `osWinSvr2008` | Windows Server 2008. |
| `osWinSvr2008R2` [v3.1]| Windows Server 2008 R 2. |
| `osWinSvr2012` [v3.4] | Windows Server 2012. |
| `osWinSvr2012R2` [v5.0] | Windows Server 2012 R 2. - will only be returned if the host application is "manifested" as a Windows 8.1 / Windows 2012 R 2 application, otherwise `osWinSvr2012` will be returned for both Windows Server 2012 and Windows Server 2012. |
| `osWinLater` | An unknown version of Windows released after the most recent version of Windows identified above. |
| `osUnknownWinNT` | An unknown product on the Windows NT platform. |
| `osUnknownWin9x` | An unknown product on the Windows 9x platform. |
| `osUnknownWin32s` | An operating system running on the Win32s platform. |
| `osUnknown` | An unknown operating system on an unknown platform. |

To find the string representation of the product name use the _[ProductName](TPJOSInfoProductName.md)_ method.

When the program is run in compatibility mode, this method will return the product code of the "emulated" operating system.

[v5.0] On operating systems where _[CanSpoof](TPJOSInfoCanSpoof.md)_ returns `False` this method will return the product code of the installed operating system, regardless of any compatibility mode.
