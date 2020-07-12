# Exists class method

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

***Class:*** [_TPJEnvironmentVars_](./TPJEnvironmentVars.md)

```pascal
class function Exists(const VarName: string): Boolean;
```

## Description

Checks if a given environment variable exists in the current process.

***Parameters:***

* _VarName_ -- The name of the environment variable to be tested.

***Returns***

* `True` if the environment variable exists or `False` if it does not.

> **Important:** Don't be tempted to simply check if the [_GetValue_](./TPJEnvironmentVars-GetValue.md) method returns the empty string to determine whether an environment variable exists or not. [_GetValue_](./TPJEnvironmentVars-GetValue.md) will return the empty string in two cases: (1) if the environment variable exists but has an empty value and (2) if the environment variable does not exist. _Exists_ returns `True` in the former case and `False` in the latter.
