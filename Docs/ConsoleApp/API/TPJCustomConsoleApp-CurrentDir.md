# CurrentDir property

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
property CurrentDir: string;
```

## Description

_CurrentDir_ is used to specify the current directory of a console application to be executed by the parameterless version of the [_Execute_](./TPJCustomConsoleApp-Execute.md) method.

If the property is set to the empty string (the default) then the console application is executed with the same current directory as its parent program.

## Remarks

If [_Execute_](./TPJCustomConsoleApp-Execute.md) is called with _CmdLine_ and _CurrentDir_ parameters then this property is set to the value of the _CurrentDir_ parameter.

The property is public in [_TPJConsoleApp_](./TPJConsoleApp.md) and protected in [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md).
