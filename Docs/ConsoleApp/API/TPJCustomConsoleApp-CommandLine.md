# CommandLine property

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
property CommandLine: string;
```

## Description

_CommandLine_ specifies the command line to be executed when the [_Execute_](./TPJCustomConsoleApp-Execute.md) method is called with no parameters.

The property includes the program name and any parameters to be passed to the program. Paths containing spaces must be quoted.

## Remarks

If _CommandLine_ is to be used with a the parameterless version of the [_Execute_](./TPJCustomConsoleApp-Execute.md) method then it must be set to some suitable value - it can't be left with its default empty string value.

If [_Execute_](./TPJCustomConsoleApp-Execute.md) is called with a _CmdLine_ parameter then _CommandLine_ is set to the value of the parameter.

The property is public in [_TPJConsoleApp_](./TPJConsoleApp.md) and protected in [_TPJCustomConsoleApp_](TPJCustomConsoleApp.md).
