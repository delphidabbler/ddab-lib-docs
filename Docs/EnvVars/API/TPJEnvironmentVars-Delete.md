# Delete class method

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

***Class:*** [_TPJEnvironmentVars_](./TPJEnvironmentVars.md)

```pascal
class function Delete(const VarName: string): Integer;
```

## Description

Deletes the environment variable with the given name in the current process. If the environment variable does not exist the method does nothing.

***Parameters:***

* _VarName_ -- The name of the environment variable to be deleted.

***Returns:***

* `0` on success or a Windows error code on failure.

 A description of any error can be found by passing the returned error code to _SysErrorMessage_ from the _SysUtils_ or _System.SysUtils_ unit.

> **Note:** This method does not update the system's environment variables, only the copy of the environment maintained by this program. Changes are lost when the program terminates.
