# UnicodeEnvironment property

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

***Introduced:*** v3.1

```pascal
property UnicodeEnvironment: Boolen;
```

## Description

This property is use to specify the environment variables in the block pointed to by the [_Environment_](./TPJCustomConsoleApp-Environment.md) property are stored as Unicode (_True_) or as ANSI text (_False_).

The default value is `False`.

## Remarks

The property is public in [_TPJConsoleApp_](TPJConsoleApp.md) and protected in [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md).
