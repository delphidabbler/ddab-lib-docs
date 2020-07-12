# GetValue class method

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

***Class:*** [_TPJEnvironmentVars_](./TPJEnvironmentVars.md)

```pascal
class function GetValue(const VarName: string): string;
```

## Description

Returns the value of a given environment variable.

***Parameters:***

* _VarName_ -- The name of the environment variable whose value is required.

***Returns***

* The required value. If the environment variable has no value or does not exist then the empty string is returned.

> **Important:** Because _GetValue_ returns the empty string both for environment variables that exist but have no value _and_ for those that do not exist, you can't use this method to check if an environment variable exists in the environment block. Use the [_Exists_](./TPJEnvironmentVars-Exists.md) method for this purpose.
