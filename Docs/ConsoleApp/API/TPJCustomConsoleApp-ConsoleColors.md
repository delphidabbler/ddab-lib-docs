# ConsoleColors property

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
property ConsoleColors: TPJConsoleColors;
```

## Description

This property determines the foreground and background colours of a console window. It is of type [_TPJConsoleColors_](./TPJConsoleColors.md), which is a record with fields for both colours. Colours must be from the 16 basic system colours and are specified using the [_TPJConsoleColor_](./TPJConsoleColor.md) enumeration.

Default values are _ccWhite_ for the foreground colour and _ccBlack_ for the background.

## Remarks

If a console application shares a console this property has no effect. See [_UseNewConsole_](./TPJCustomConsoleApp-UseNewConsole.md) for more information about shared consoles.

The individual fields of the property are read-only so the property must be set by first creating a [_TPJConsoleColors_](./TPJConsoleColors.md) record containing the required foreground and background colours and then assigning the record to the property. For example:

```pascal
var
  Colors: TPJConsoleColors;
  App: TPJConsoleApp;
begin
  // assume App contains a valid TPJConsoleApp instance
  Colors.Foreground := ccYellow;
  Colors.Background := ccNavy;
  App.ConsoleColors := Colors;
end;
```

The [_MakeConsoleColors_](./Routines.md#makeconsolecolors) routine has been provided to make this process easier. The following code has the same effect as the above:

```pascal
var
  App: TPJConsoleApp;
begin
  // assume App contains a valid TPJConsoleApp instance
  App.ConsoleColors := MakeConsoleColors(ccYellow, ccNavy);
end;
```

The property is public in [_TPJConsoleApp_](./TPJConsoleApp.md) and protected in [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md).
