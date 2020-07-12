# SetValue class method

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

***Class:*** [_TPJEnvironmentVars_](./TPJEnvironmentVars.md)

```pascal
class function SetValue(const VarName, VarValue: string): Integer;
```

## Description

Sets the value of a given environment variable for the current process. If the environment variable does not exist then it is created.

***Parameters:***

* _VarName_ -- The name of the environment variable whose value is to be set. Must not be the empty string.
* _VarValue_ -- The environment variable's new value.

***Returns:***

* `0` on success or a Windows error code on failure.

The most likely causes of error are attempting to set the value of an un-named environment variable or when the environment block is full and there is no room for the new value or to create a new variable. A description of any error can be found by passing the error code to _SysErrorMessage_ from the _SysUtils_ or _System.SysUtils_ unit.

> **Important:** Setting an environment variable to the empty string does not delete it from the environment block: use the [_Delete_](./TPJEnvironmentVars-Delete.md) method to do that.
>
> **Note:** This method does not update the system's environment variables, only the copy of the environment maintained by this program. Changes are lost when the program terminates.
