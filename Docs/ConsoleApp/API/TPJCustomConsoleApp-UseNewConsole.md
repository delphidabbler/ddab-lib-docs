# UseNewConsole property

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
property UseNewConsole: Boolean;
```

## Description

_UseNewConsole_ determines whether a console application is run in a new console window or whether it shares any console of the parent application.

Set _UseNewConsole_ to _True_ if you want the child console application process to be started in a new console window. Set the property to _False_ to force the child process to use the same console as the parent.

If the parent process does not have a console window (for example in a GUI program) then the child process ***always*** gets a new console window regardless of the value of _UseNewConsole_.

The property defaults to False.

## Remarks

Whether any new console window is actually displayed depends on the value of the [_Visible_](./TPJCustomConsoleApp-Visible.md) property.

The characteristics of a new console window can be customised using the following properties:

* [_ConsoleColors_](./TPJCustomConsoleApp-ConsoleColors.md)
* [_ConsoleTitle_](./TPJCustomConsoleApp-ConsoleTitle.md)
* [_ScreenBufferSize_](./TPJCustomConsoleApp-ScreenBufferSize.md)
* [_Visible_](./TPJCustomConsoleApp-Visible.md)
* [_WindowPosition_](./TPJCustomConsoleApp-WindowPosition.md)
* [_WindowSize_](./TPJCustomConsoleApp-WindowSize.md)

These properties are ignored if the console application shares the parent's console.

The property is public in [_TPJConsoleApp_](./TPJConsoleApp.md) and protected in [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md).
