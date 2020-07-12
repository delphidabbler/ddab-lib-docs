# DeleteVar method

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

***Class:*** [_TPJEnvVars_](./TPJEnvVars.md)

```pascal
procedure DeleteVar(const Name: string);
```

> ***Warning:*** *[_TPJEnvVars_](./TPJEnvVars.md) has been **deprecated**. Use the [_TPJEnvironmentVars.Delete_](./TPJEnvironmentVars-Delete.md) static method in preference.*

## Description

Deletes the environment variable with the given name.

***Parameters:***

* _Name_ -- The name of the environment variable to be deleted.

A [_EPJEnvVars_](./EPJEnvVars.md) exception is raised if it is not possible to delete the variable.

> **Note:** This method **does not** update the system's environment variables, only the copy of the environment maintained by this program. Changes are lost when the program terminates.
