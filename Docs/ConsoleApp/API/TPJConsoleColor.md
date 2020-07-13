# TPJConsoleColor type

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

```pascal
type
  TPJConsoleColor = (
    ccBlack   =  0,  ccNavy    =  1,  ccGreen   =  2,  ccTeal    =  3,
    ccMaroon  =  4,  ccPurple  =  5,  ccOlive   =  6,  ccSilver  =  7,
    ccGray    =  8,  ccBlue    =  9,  ccLime    = 10,  ccAqua    = 11,
    ccRed     = 12,  ccFuchsia = 13,  ccYellow  = 14,  ccWhite   = 15
  );
```

## Description

This is an enumeration of all possible colours that can be used for a console's foreground and background.

## Remarks

It is important that the assigned ordinal values are retained. They relate to various combinations of the *FOREGROUND_xxx* constants declared in the _Windows_ unit. Foreground colours are obtained directly from these ordinal values while background colours are obtained by left shifting the values by 4.

The value names are similar to the equivalent _TColor_ constants, but have different numeric values. Colours with similar value names display the same colours. For example `ccBlue` displays the same colour in a console as `clBlue` does in a GUI application's forms.

## See Also

* [_TPJConsoleColors_](./TPJConsoleColors.md) record.
* [_TPJConsoleApp.ConsoleColors_](TPJCustomConsoleApp-ConsoleColors.md) property.
* [Type Definitions List](./Types.md)
