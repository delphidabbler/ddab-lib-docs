<a href='Hidden comment: 
$Rev$
$Date$
'></a>

Project: [System Information Unit](SystemInformationUnit.md)

Unit: _PJSysInfo_.

# PJSysInfo Global Variables #

The _PJSysInfo_ unit defines several global variables containing extended operating system information. These variables build on similar _Win32XXX_ variables defined in the _SysUtils unit_.

The variables defined in _PJSysInfo_ are:

  * [Win32PlatformEx](#Win32PlatformEx.md) [v5.0]
  * [Win32MajorVersionEx](#Win32MajorVersionEx.md) [v5.0]
  * [Win32MinorVersionEx](#Win32MinorVersionEx.md) [v5.0]
  * [Win32BuildNumberEx](#Win32BuildNumberEx.md) [v5.0]
  * [Win32CSDVersionEx](#Win32CSDVersionEx.md) [v5.0]
  * [Win32HaveExInfo](#Win32HaveExInfo.md)
  * [Win32ServicePackMajor](#Win32ServicePackMajor.md)
  * [Win32ServicePackMinor](#Win32ServicePackMinor.md)
  * [Win32SuiteMask](#Win32SuiteMask.md)
  * [Win32ProductType](#Win32ProductType.md)
  * [Win32HaveProductInfo](#Win32HaveProductInfo.md)
  * [Win32ProductInfo](#Win32ProductInfo.md)


## Win32PlatformEx ##

**Introduced:** v5.0

```
var Win32PlatformEx: Integer;
```

_Win32PlatformEx_ records the current operating system platform. This is one of `VER_PLATFORM_WIN32_NT`, `VER_PLATFORM_WIN32_WINDOWS` or (very unlikely) `VER_PLATFORM_WIN32s`.

This variable is an analogue of _Win32Platform_ variable defined in _SysUtils_ except that, on operating systems that support it, _Win32PlatformEx_'s value is not spoofed when the program is running in compatibility mode.

Whether _Win32PlatformEx_ can be spoofed depends on the value returned by _[TPJOSInfo.CanSpoof](TPJOSInfoCanSpoof.md)_. A value of `False` means _Win32PlatformEx_ returns the correct platform for the host operating system while `True` means that _Win32PlatformEx_ is spoofed by compatibility mode into returning the platform represented by the emulated operating system.

_Win32Platform_, on the other hand, is always spoofed by compatibility mode.


## Win32MajorVersionEx ##

**Introduced:** v5.0

```
var Win32MajorVersionEx: LongWord;
```

Records the major version number of the operating system.

This variable is an analogue of _Win32MajorVersion_ variable defined in _SysUtils_ except that, on operating systems that support it, _Win32MajorVersionEx_'s value is not spoofed when the program is running in compatibility mode, whereas _Win32MajorVersion_ is always spoofed in these circumstances.

Whether _Win32MajorVersionEx_ can be spoofed depends on the value returned by _[TPJOSInfo.CanSpoof](TPJOSInfoCanSpoof.md)_. A value of `False` means _Win32MajorVersionEx_ returns the correct major version number for the host operating system while `True` means that _Win32MajorVersionEx_ is spoofed by compatibility mode into returning the major version represented by the emulated operating system.


## Win32MinorVersionEx ##

**Introduced:** v5.0

```
var Win32MinorVersionEx: LongWord;
```

Records the minor version number of the operating system.

This variable is an analogue of _Win32MinorVersion_ variable defined in _SysUtils_ except that, on operating systems that support it, _Win32MinorVersionEx_'s value is not spoofed when the program is running in compatibility mode, whereas _Win32MinorVersion_ is always spoofed in these circumstances.

Whether _Win32MinorVersionEx_ can be spoofed depends on the value returned by _[TPJOSInfo.CanSpoof](TPJOSInfoCanSpoof.md)_. A value of `False` means _Win32MinorVersionEx_ returns the correct minor version number for the host operating system while `True` means that _Win32MinorVersionEx_ is spoofed by compatibility mode into returning the minor version represented by the emulated operating system.


## Win32BuildNumberEx ##

**Introduced:** v5.0

```
var Win32BuildNumberEx: Integer;
```

Records the build number of the operating system.

This variable is an analogue of _Win32BuildNumber_ variable defined in _SysUtils_ except that, on operating systems that support it, _Win32BuildNumberEx_'s value is not spoofed when the program is running in compatibility mode. _Win32BuildNumber_ is always spoofed in these circumstances.

Whether _Win32BuildNumberEx_ can be spoofed depends on the value returned by _[TPJOSInfo.CanSpoof](TPJOSInfoCanSpoof.md)_. A value of `False` means _Win32BuildNumberEx_ returns the correct build number for the host operating system while `True` means that _Win32BuildNumberEx_ is spoofed by compatibility mode into returning the build number represented by the emulated operating system.


## Win32CSDVersionEx ##

**Introduced:** v5.0

```
var Win32CSDVersionEx: string;
```

Stores the name of any service pack applied to the operating system. The value is the empty string if there is no service pack.

This variable is an analogue of _Win32CSDVersion_ variable defined in _SysUtils_ except that, on operating systems that support it, _Win32CSDVersionEx_'s value is not spoofed when the program is running in compatibility mode. _Win32CSDVersion_ is always spoofed in these circumstances.

Whether _Win32CSDVersionEx_ can be spoofed depends on the value returned by _[TPJOSInfo.CanSpoof](TPJOSInfoCanSpoof.md)_. A value of `False` means _Win32CSDVersionEx_ returns the correct service pack string for the host operating system while `True` means that _Win32CSDVersionEx_ is spoofed by compatibility mode into returning the service pack of the emulated operating system.


## Win32HaveExInfo ##

```
var Win32HaveExInfo: Boolean;
```

This global variable is `True` if extended operating system information is available and `False` if not. When `False` the values of the _[Win32ServicePackMajor](#Win32ServicePackMajor.md)_, _[Win32ServicePackMinor](#Win32ServicePackMinor.md)_, _[Win32SuiteMask](#Win32SuiteMask.md)_ and _[Win32ProductType](#Win32ProductType.md)_ variables are not valid and should not be used.

Extended operating system information is available only on Windows NT platform operating systems from and including Windows NT4 Service Pack 6.

Compatibility modes have no effect on _Win32HaveExInfo_: its value depends on the capabilities of the actual operating system, even in cases where the emulated operating system would not natively support extended information.


## Win32ServicePackMajor ##

```
var Win32ServicePackMajor: string;
```

This global variable stores the major version number the operating system's service pack or `0` if the OS has no service pack applied.

Note that this variable only stores valid information if the _[Win32HaveExInfo](#Win32HaveExInfo.md)_ variable is `True`.

Running the host program in compatibility mode _Win32ServicePackMajor_ is always spoofed to return the major version of any service pack that relates to the emulated operating system.

[v5.0] When running on operating systems where _[TPJOSInfo.CanSpoof](TPJOSInfoCanSpoof.md)_ returns `False`, compatibility mode no longer spoofs _Win32ServicePackMajor_ and it will return the service pack major version of the actual operating system.


## Win32ServicePackMinor ##

```
var Win32ServicePackMinor: string;
```

This global variable stores any minor version number the operating system's service pack. If _Win32ServicePackMajor_ returns `0` then _Win32ServicePackMinor_ will also return `0`.

Note that this variable only stores valid information if the _[Win32HaveExInfo](#Win32HaveExInfo.md)_ variable is `True`.

Running the host program in compatibility mode _Win32ServicePackMinor_ is always spoofed to return the minor version of any service pack that relates to the emulated operating system.

[v5.0] When running on operating systems where _[TPJOSInfo.CanSpoof](TPJOSInfoCanSpoof.md)_ returns `False`, compatibility mode no longer spoofs _Win32ServicePackMinor_ and it will return the service pack minor version of the actual operating system.


## Win32SuiteMask ##

```
var Win32SuiteMask: Integer;
```

This global variable stores a combination of bit flags that identify the product suites available on the system. The value is a combination of _VER\_SUITE\_xxx_ constants that are defined by Microsoft. The constants are declared in the _PJSysInfo_ unit.

Note that this variable only stores valid information if the _[Win32HaveExInfo](#Win32HaveExInfo.md)_ variable is true.

Compatibility mode has no effect on this value.

[v5.0] When running on operating systems where _[TPJOSInfo.CanSpoof](TPJOSInfoCanSpoof.md)_ returns `False` _Win32SuiteMask_ always returns `0`. You should get product information from the _[Win32ProductInfo](#Win32ProductInfo.md)_ instead.


## Win32ProductType ##

```
var Win32ProductType: Integer;
```

This global variable stores additional information about an operating system product.a. The value one of the _VER\_NT\_xxx_ constants defined by Microsoft. The constants are declared in the _PJSysInfo_ unit.

Note that this variable only stores valid information if the _[Win32HaveExInfo](#Win32HaveExInfo.md)_ variable is true.

Compatibility mode has no effect on this value: running an emulation of a server operating system on a desktop system leaves _Win32ProductType_ with the value of `VER_NT_WORKSTATION` instead of changing it to `VER_NT_SERVER` as would be the case for a genuine server operating system.


## Win32HaveProductInfo ##

```
var Win32HaveProductInfo: Boolean;
```

This global variable informs whether product information is available from the operating system. Such information is obtained from the Windows API function _GetProductInfo_, which is available on Windows Vista and later operating systems.

When _Win32HaveProductInfo_ is True the product information code can be read from _[Win32ProductInfo](#Win32ProductInfo.md)_, otherwise _Win32ProductInfo_ is set to 0.

Compatibility modes have no effect on _Win32HaveProductInfo_: its value depends on the capabilities of the actual operating system, even in cases where the emulated operating system would not natively support the required API functions.


## Win32ProductInfo ##

```
var Win32ProductInfo: LongWord;
```

This global variable provides additional product information about the operating system. The value is one of the _PRODUCT\_xxx_ constants defined by Microsoft. The constants are declared in the _PJSysInfo_ unit.

Note that this variable only stores valid information if the _[Win32HaveProductInfo](#Win32HaveProductInfo.md)_ variable is true, otherwise _Win32ProductInfo_ is set to 0.

Running the host program in compatibility mode _Win32ProductInfo_ is always spoofed to return the product information that relates to the emulated operating system. If the emulated operating system did not expose product information in this way the value will be `0`.

[v5.0] When running on operating systems where _[TPJOSInfo.CanSpoof](TPJOSInfoCanSpoof.md)_ returns `False`, compatibility mode no longer spoofs _Win32ProductInfo_ and it will return product information relating to the actual operating system.