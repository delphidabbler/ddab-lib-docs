# Execute method

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
function Execute(const CmdLine, CurrentDir: string = _): Boolean; overload;
```

*Introduced v2.0:*

```pascal
function Execute: Boolean; overload;
```

## Description

Executes the command line application.

The first, original version of the method has the command line and (optionally) the current directory passed as parameters:

* _CmdLine_: Command line to be executed. This should include the name of the application (with path if necessary) along with any required parameters. Paths and parameters containing spaces should be enclosed in double quotes.
* _CurrentDir_: The directory that the application is to treat as its current directory.

The second, parameterless, version of the method was introduced in version 2. It executes the command line specified by the [_CommandLine_](./TPJCustomConsoleApp-CommandLine.md) property with the current directory specified by the [_CurrentDir_](TPJCustomConsoleApp-CurrentDir.md) property.

_Execute_ returns _True_ if the application was executed successfully and _False_ if the application failed to run. When _False_ is returned, the [_ErrorCode_](./TPJCustomConsoleApp-ErrorCode.md) property will contain a non-zero error code.

## Remarks

If the current directory (however specified) is the empty string then the executed application's current directory will be that of its parent process.

If the _CmdLine_ parameter is specified then the [_CommandLine_](TPJCustomConsoleApp-CommandLine.md) property will be updated to the same value.

Similarly the [_CurrentDir_](TPJCustomConsoleApp-CurrentDir.md) property receives the value of any _CurrentDir_ parameter.
