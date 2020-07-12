# GetEnumerator method

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

***Class:*** [_TPJEnvVars_](./TPJEnvVars.md)

```pascal
function GetEnumerator: TPJEnvVarsEnumerator;
```

***Warning:*** *[_TPJEnvVars_](./TPJEnvVars.md) has been **deprecated***. Use [_TPJEnvVarsEnumerator_](./TPJEnvVarsEnumerator.md) instances directly or use [_TPJEnvironmentVars.EnumNames_](./TPJEnvironmentVars-EnumNames.md) static method instead.

## Description

Creates and returns a new enumerator of all environment variable names in the current process.

***Returns:***

* A new [_TPJEnvVarsEnumerator_](./TPJEnvVarsEnumerator.md) instance. When the method is called manually the user is responsible for freeing the instance.

When compiled with Delphi 2005 and this method enables a [_TPJEnvVars_](./TPJEnvVars.md) component instance to be used in a `for..in` loop.

> **Important:** Environment variables should not be modified while the enumerator is executing (e.g. in a `for..in` loop).
