# ErrorCode property

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
property ErrorCode: LongWord;
```

## Description

This read only property provides information about any error that occurred while attempting to run a console application. The property is set to zero if the application was executed successfully.

Error codes either correspond to Windows error codes or are set by this class. Error codes set by the class have bit 29 set†. The error codes specific to the console application runner classes are:

| Error code (hex) | Constant | Description |
|------------------|----------|-------------|
| `$20000001` | [_cAppErrorTimeOut_](./Constants.md#capperrortimeout) | Application timed out (see the [_MaxExecTime_](./TPJCustomConsoleApp-MaxExecTime.md) property). |
| `$20000002` | [_cAppErrorTerminated_](./Constants.md#capperrorterminated) | Application was forcibly terminated (see the [_Terminate_](./TPJCustomConsoleApp-Terminate.md) method). |

† According to the Windows API documentation, error codes with bit 29 set are reserved for application use.

## Remarks

This property only represents errors in executing the console application (for example program not found, timed-out, terminated etc.). Errors that occur within the application are not reported via _ErrorCode_. Console applications usually report such errors via their exit code. The exit code is exposed via the [_ExitCode_](./TPJCustomConsoleApp-ExitCode.md) property.

To check for application errors, use the constants from the table and AND them with the [_cAppErrorMask_](./Constants.md#capperrormask) constant. For example:

```pascal
if (ErrorCode and cAppErrorTimeout) <> 0 then
  // Do something;
```

> Alternatively use the [_IsApplicationError_](./Routines.md#isapplicationerror) function to check for application errors.

The property is public in [_TPJConsoleApp_](./TPJConsoleApp.md) and protected in [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md).
