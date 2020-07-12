# TPJEnvVarsEnumEx method type

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

```pascal
type
  TPJEnvVarsEnumEx =
    {$IFNDEF Supports_Closures}
    procedure(const EnvVar: TPJEnvironmentVar; Data: Pointer) of object;
    {$ELSE}
    reference to procedure(const EnvVar: TPJEnvironmentVar; Data: Pointer);
    {$ENDIF}
```

## Description

_TPJEnvVarsEnumEx_ defines the type of callback method that is called when enumerating both the names and values environment variables. Callbacks of this type are used in the [_TPJEnvironmentVars.EnumVars_](./TPJEnvironmentVars-EnumVars.md) method.

If the compiler supports anonymous methods (a.k.a. closures) then the `Supports_Closures` symbol is defined and _TPJEnvVarsEnumEx_ is an anonymous method. Otherwise the `Supports_Closures` symbol is undefined and _TPJEnvVarsEnumEx_ is a normal method

Regardless of how _TPJEnvVarsEnumEx_ is defined the parameters are the same.

***Parameters:***

* _EnvVar_ -- [_TPJEnvironmentVar_](./TPJEnvironmentVar.md) record containing the name and value of the current environment variable in the enumeration.

* _Data_ - User-specified value that was passed to [_TPJEnvironmentVars.EnumVars_](./TPJEnvironmentVars-EnumVars.md). How (or if) this value is interpreted is implementation defined.

> **Important:** Callback methods should not add, modify or delete environment variables since this can lead to obscure bugs in the enumeration.
