# TPJConsoleAppPriority type

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

```pascal
type
  TPJConsoleAppPriority = (
    cpDefault, cpHigh, cpNormal, cpIdle, cpRealTime
  );
```

## Description

_TPJConsoleAppPriority_ is the type of the [_TPJCustomConsoleApp.Priority_](./TPJCustomConsoleApp-Priority.md) property. It defines values for each possible priority level with which an application can be executed.

Values are:

| Value | Description |
|-------|-------------|
| _cpDefault_ | Default priority. Normally _cpNormal_ is used unless the parent process has priority _cpIdle_ in which case _cpIdle_ is used. |
| _cpHigh_ | High priority. Use for time-critical tasks (processor intensive). |
| _cpNormal_ | Normal priority for applications with no specific scheduling needs. |
| _cpIdle_ | Idle priority. The process is run only when the system is idle. |
| _cpRealTime_ | Real time priority. Highest possible priority (pre-empts all threads, including the operating system). |

## See Also

* [Type Definitions List](./Types.md)
* [Programmers' Guide](../API.md)
