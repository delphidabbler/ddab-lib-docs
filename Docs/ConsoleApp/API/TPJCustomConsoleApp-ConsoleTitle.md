# ConsoleTitle property

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
property ConsoleTitle: string;
```

## Description

This property determines the title to be displayed by a console application's window. If the property is set to the empty string then the console window's default title is used.

The property defaults to the empty string.

## Remarks

If a console application shares a console this property has no effect. See [_UseNewConsole_](./TPJCustomConsoleApp-UseNewConsole.md) for more information about shared consoles.

The property is public in [_TPJConsoleApp_](./TPJConsoleApp.md) and protected in [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md).
