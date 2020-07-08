# Visible property

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
property Visible: Boolean;
```

## Description

This property determines whether the console application's console window is to be displayed.

When _Visible_ is _True_ then any console window is displayed. When the property is _False_ the console window is hidden.

This property defaults to _False_.

## Remarks

Setting the _Visible_ property to _False_ does not prevent a console window from being created, it is just not displayed.

If a console application shares a console this property has no effect. See [_UseNewConsole_](./TPJCustomConsoleApp-UseNewConsole.md) for more information about shared consoles.

The property is public in [_TPJConsoleApp_](./TPJConsoleApp.md) and protected in [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md).
