# EnumNames method

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

***Class:*** [_TPJEnvVars_](./TPJEnvVars.md)

```pascal
procedure EnumNames(Callback: TPJEnvVarsEnum; Data: Pointer);
```

> ***Warning:*** *[_TPJEnvVars_](./TPJEnvVars.md) has been **deprecated**. Use the  [_TPJEnvironmentVars.EnumNames_](./TPJEnvironmentVars-EnumNames.md) static method instead.*

## Description

Enumerates the names of all the environment variables in the current process.

***Parameters:***

* _Callback_ -- Method or (for Delphi 2009 or later) anonymous procedure of type [_TPJEnvVarsEnum_](./TPJEnvVarsEnum.md) that is called once for each environment variable and is passed the the environment variable's name and the value of the _Data_ parameter.
* _Data_ -- Pointer passed to _Callback_ each time it is called. The purpose of this value is user-defined and has no meaning to _EnumNames_.

The _Callback_ method or (anonymous procedure) must be implemented by the caller.

> **Important:** Environment variables should not be modified while _EnumNames_ is executing. This is because the method takes a snap-shot of the environment variable names before it starts calling _Callback_. Any environment variables added or deleted while _EnumNames_ is running will not be reflected in the enumeration and could cause obscure bugs.
