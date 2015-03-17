# MACAddress class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJComputerInfo](TPJComputerInfo.md)_

```pascal
class function MACAddress: string;
```

## Description ##

Returns the address of the first network card found in the host computer. The empty string is returned if no network card is detected.

If no network card is active then the MAC Address will not be detected. Furthermore NETBIOS must be enabled for TCP on the network card.

Microsoft notes that NETBIOS is not available Windows Vista and later, however tests show the method works on Vista SP1 with NETBIOS enabled.

Microsoft also note that this method of detecting MAC addresses may not work reliably on Windows 95, 98 and Me.

**Use with care**