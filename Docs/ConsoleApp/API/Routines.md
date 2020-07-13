# Helper Routines

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

The following routines are declared in the library:

* [_IsApplicationError_](#isapplicationerror)
* [_MakeConsoleColors_](#makeconsolecolors)
* [_MakeSize_](#makesize)

## IsApplicationError

```pascal
function IsApplicationError(const ErrCode: LongWord): Boolean;
```

### IsApplicationError description

Checks if error code _ErrCode_ is an application defined error. Returns `True` if the error is application defined, `False` if not.

### IsApplicationError remarks

Application defined error codes have bit 29 set per Windows recommendations.

Use this routine to test error codes that are stored in the [_ErrorCode_](./TPJCustomConsoleApp-ErrorCode.md) property of [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md).

## MakeConsoleColors

```pascal
function MakeConsoleColors(const AForeground, ABackground: TPJConsoleColor):
  TPJConsoleColors; overload;

function MakeConsoleColors(const AForeground, ABackground: TColor):
  TPJConsoleColors; overload;

function MakeConsoleColors(const AForeground, ABackground: TAlphaColor):
  TPJConsoleColors; overload;
```

### MakeConsoleColors description

Three overloaded "constructor" functions, each of which creates an initialised [_TPJConsoleColors_](./TPJConsoleColors.md) record from the foreground and background colours specified by the _AForeground_ and _ABackground_ parameters.

The first of the routines with the [_TPJConsoleColor_](./TPJConsoleColor.md) parameters assigns the parameters directly to the fields of the [_TPJConsoleColors_](./TPJConsoleColors.md) record.

The second of the routines with the _TColor_ parameters first converts the _TColor_ values to the equivalent [_TPJConsoleColor_](./TPJConsoleColor.md) before assigning the resulting record's fields. This function is provided as a convenience to enable uses to initialise a [_TPJConsoleColors_](./TPJConsoleColors.md) record directly from _TColor_ values without having to convert to a [_TPJConsoleColor_](./TPJConsoleColor.md) value manually.

The third, _TAlphaColor_, overload. This function is similar to the _TColor_ override above, except that it converts _TAlphaColor_ values to the equivalent [_TPJConsoleColor_](./TPJConsoleColor.md) value.

> The _TAlphaColor_ overload is available only when compiling with Delphi XE2 or later.

These functions are provided because it is not possible to assign the fields of the [_TPJConsoleApp.ConsoleColors_](TPJCustomConsoleApp-ConsoleColors.md) property individually. Instead assign the return value of one of these functions to the property.

An exception is raised if either the _TColor_ or _TAlphaColor_ versions of the routine is passed any colour value that is not one of the 16 standard colours that correspond to the colours in the [_TPJConsoleColor_](./TPJConsoleColor.md) enumeration.

## MakeSize

```pascal
function MakeSize(const ACX, ACY: LongInt): TSize;
```

### MakeSize description

This is a "constructor" function that creates initialised _TSize_ records.

> This function is provided because if is not possible to assign the fields of properties of type _TSize_ individually. Instead assign the return value of this function to such properties.
