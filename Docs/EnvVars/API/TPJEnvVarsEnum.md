# TPJEnvVarsEnum method type

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

```pascal
type
  TPJEnvVarsEnum =
    {$IFNDEF Supports_Closures}
    procedure(const VarName: string; Data: Pointer) of object;
    {$ELSE}
    reference to procedure(const VarName: string; Data: Pointer);
    {$ENDIF}
```

## Description

_TPJEnvVarsEnum_ defines the type of callback method that is called when enumerating environment variable names. Callbacks of this type are used in the [_TPJEnvironmentVars.EnumNames_](./TPJEnvironmentVars-EnumNames.md) and ***deprecated*** [_TPJEnvVars.EnumNames_](./TPJEnvVars-EnumNames.md) methods.

If the compiler supports anonymous methods (a.k.a. closures) then the `Supports_Closures` symbol is defined and _TPJEnvVarsEnum_ is an anonymous method. Otherwise the `Supports_Closures` symbol is undefined and _TPJEnvVarsEnum_ is a normal method

Regardless of how _TPJEnvVarsEnum_ is defined the parameters are the same.

***Parameters:***

* _VarName_ -- The name of the current environment variable in the enumeration.

* _Data_ -- User-specified value that was passed to [_TPJEnvironmentVars.EnumNames_](./TPJEnvironmentVars-EnumNames.md) or [_TPJEnvVars.EnumNames_](./TPJEnvVars-EnumNames.md). If or how this value is interpreted is left to the caller.

> **Important:** Callback methods should not add, modify or delete environment variables since this can lead to obscure bugs in the enumeration.
